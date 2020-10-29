## keepersecurity

### Here follows some commands I use to test and prefer to keep together with the repo for quick copy and paste:
```bash
sudo zypper install flatpak flatpak-builder
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
sudo flatpak -y --system install flathub org.freedesktop.Platform//20.08 org.freedesktop.Sdk//20.08

# BUILD
flatpak-builder --force-clean --repo=test-repo-keepersecurity build-dir com.keepersecurity.vault.json

# TEST
sudo flatpak remote-add --no-gpg-verify test-repo-keepersecurity test-repo-keepersecurity
flatpak -y remove com.keepersecurity.vault
flatpak -y --system install test-repo-keepersecurity com.keepersecurity.vault
flatpak run com.keepersecurity.vault
flatpak run --command=/bin/bash com.keepersecurity.vault

# EXPORT
flatpak build-bundle test-repo-keepersecurity keepersecurity-15.0.6.flatpak com.keepersecurity.vault

# IMPORT
sudo flatpak -y install keepersecurity-15.0.6.flatpak
sudo flatpak -y remove com.keepersecurity.vault

```

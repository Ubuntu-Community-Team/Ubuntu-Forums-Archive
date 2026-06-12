---
title: "Help: System is broken"
date: 2024-04-20
forum: Installation &amp; Upgrades
---

### Post by pamparana on 2024-04-20
My ubuntu (22.04.4 LTS) reported it can doa  apartial update and then crashed while configuring libssl3.

Now, I cannot do any updates. 

Running ```
[sudo dpkg --configure -a
```

returns 
```

dpkg: dependency problems prevent configuration of openssh-sftp-server:
 openssh-sftp-server depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package openssh-sftp-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tcpdump:
 tcpdump depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package tcpdump (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmysqlclient21:amd64:
 libmysqlclient21:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libmysqlclient21:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mokutil:
 mokutil depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package mokutil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openvpn:
 openvpn depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package openvpn (--configure):
 dependency problems - leaving unconfigured
Setting up initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: deferring update (trigger activated)
Setting up liblibreoffice-java (1:7.3.7-0ubuntu0.22.04.4) ...
Setting up grub-efi-amd64-signed (1.187.6+2.06-2ubuntu14.4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-sftp-server; however:
  Package openssh-sftp-server is not configured yet.
 openssh-server depends on libssl3 (>= 3.0.2); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package openssh-server (--configure):
 dependency problems - leaving unconfigured
Setting up libjurt-java (1:7.3.7-0ubuntu0.22.04.4) ...
dpkg: dependency problems prevent configuration of bind9-libs:amd64:
 bind9-libs:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package bind9-libs:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-client:
 openssh-client depends on libssl3 (>= 3.0.2); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package openssh-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp2-2:amd64:
 libfreerdp2-2:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libfreerdp2-2:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libssl3:i386 (3.0.2-0ubuntu1.15) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libssl3:i386 (--configure):
 installed libssl3:i386 package post-installation script subprocess returned error exit status 1
Setting up nvidia-dkms-550 (550.54.15-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-5.15.0-79-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p1
I: (UUID=62dd32c9-2b5c-4ee8-bed6-50fc8fe0176b)
I: Set the RESUME variable to override this.
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package nvidia-dkms-550 (--configure):
 installed nvidia-dkms-550 package post-installation script subprocess returned error exit status 1
Setting up locales (2.35-0ubuntu3.7) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package locales (--configure):
 installed locales package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libwinpr2-2:amd64:
 libwinpr2-2:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libwinpr2-2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7-stdlib:amd64:
 libpython2.7-stdlib:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libpython2.7-stdlib:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up tzdata (2024a-0ubuntu0.22.04) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 1
Setting up apparmor (3.0.4-2ubuntu2.3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package apparmor (--configure):
 installed apparmor package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of transmission-gtk:
 transmission-gtk depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package transmission-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up libreoffice-common (1:7.3.7-0ubuntu0.22.04.4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libreoffice-common (--configure):
 installed libreoffice-common package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of python3-cryptography:
 python3-cryptography depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package python3-cryptography (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-dkms-530:
 nvidia-dkms-530 depends on nvidia-dkms-550; however:
  Package nvidia-dkms-550 is not configured yet.

dpkg: error processing package nvidia-dkms-530 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython3.10-minimal:amd64:
 libpython3.10-minimal:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libpython3.10-minimal:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libjuh-java (1:7.3.7-0ubuntu0.22.04.4) ...
dpkg: dependency problems prevent configuration of gnome-remote-desktop:
 gnome-remote-desktop depends on libfreerdp2-2 (>= 2.5.0); however:
  Package libfreerdp2-2:amd64 is not configured yet.
 gnome-remote-desktop depends on libwinpr2-2 (>= 2.3.0); however:
  Package libwinpr2-2:amd64 is not configured yet.

dpkg: error processing package gnome-remote-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libssh-4:amd64:
 libssh-4:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libssh-4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-common (>= 1:7.0.0~alpha~); however:
  Package libreoffice-common is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-common (>= 1:7.0.0~alpha~); however:
  Package libreoffice-common is not configured yet.

dpkg: error processing package libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-server2-2:amd64:
 libfreerdp-server2-2:amd64 depends on libfreerdp2-2 (= 2.6.1+dfsg1-3ubuntu2.5); however:
  Package libfreerdp2-2:amd64 is not configured yet.
 libfreerdp-server2-2:amd64 depends on libwinpr2-2 (>= 2.1.0+dfsg1); however:
  Package libwinpr2-2:amd64 is not configured yet.

dpkg: error processing package libfreerdp-server2-2:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libpam-systemd:amd64 (249.11-0ubuntu3.12) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam-systemd:amd64 (--configure):
 installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libcurl4:amd64:
 libcurl4:amd64 depends on libssh-4 (>= 0.9.0); however:
  Package libssh-4:amd64 is not configured yet.
 libcurl4:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libcurl4:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcryptsetup12:amd64:
 libcryptsetup12:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libcryptsetup12:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-common (>= 1:6.1.0~); however:
  Package libreoffice-common is not configured yet.
 libreoffice-help-en-us depends on libreoffice-l10n-en-us; however:
  Package libreoffice-l10n-en-us is not installed.
  Package libreoffice-common which provides libreoffice-l10n-en-us is not configured yet.

dpkg: error processing package libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:amd64:
 libkrb5-3:amd64 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package libkrb5-3:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:i386:
 libkrb5-3:i386 depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:i386 is not configured yet.

dpkg: error processing package libkrb5-3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.

dpkg: error processing package language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.15.0-105-generic:
 linux-headers-5.15.0-105-generic depends on libssl3 (>= 3.0.0~~alpha1); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package linux-headers-5.15.0-105-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of curl:
 curl depends on libcurl4 (= 7.81.0-1ubuntu1.16); however:
  Package libcurl4:amd64 is not configured yet.

dpkg: error processing package curl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-common (>= 1:7.0.0~alpha~); however:
  Package libreoffice-common is not configured yet.

dpkg: error processing package python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-dnsutils:
 bind9-dnsutils depends on bind9-libs (= 1:9.18.18-0ubuntu0.22.04.2); however:
  Package bind9-libs:amd64 is not configured yet.
 bind9-dnsutils depends on libkrb5-3 (>= 1.6.dfsg.2); however:
  Package libkrb5-3:amd64 is not configured yet.

dpkg: error processing package bind9-dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-paramiko:
 python3-paramiko depends on python3-cryptography (>= 2.5); however:
  Package python3-cryptography is not configured yet.

dpkg: error processing package python3-paramiko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on bind9-libs (= 1:9.18.18-0ubuntu0.22.04.2); however:
  Package bind9-libs:amd64 is not configured yet.

dpkg: error processing package bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl3 (>= 3.0.2-0ubuntu1.2); however:
  Package libssl3:amd64 is not configured yet.

dpkg: error processing package openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-ogltrans:
 libreoffice-ogltrans depends on libreoffice-impress (>= 1:6.2.0~beta1~); however:
  Package libreoffice-impress is not configured yet.

dpkg: error processing package libreoffice-ogltrans (--configure):
 dependency problems - leaving unconfigured
Setting up xserver-xorg-legacy (2:21.1.4-2ubuntu1.7~22.04.10) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package xserver-xorg-legacy (--configure):
 installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:7.3.7); however:
  Package libreoffice-common is not configured yet.

dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-pro-client (31.2.2~22.04) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package ubuntu-pro-client (--configure):
 installed ubuntu-pro-client package post-installation script subprocess returned error exit status 1
Setting up libridl-java (1:7.3.7-0ubuntu0.22.04.4) ...
dpkg: dependency problems prevent configuration of libfreerdp-client2-2:amd64:
 libfreerdp-client2-2:amd64 depends on libfreerdp2-2 (= 2.6.1+dfsg1-3ubuntu2.5); however:
  Package libfreerdp2-2:amd64 is not configured yet.
 libfreerdp-client2-2:amd64 depends on libwinpr2-2 (>= 2.6.1+dfsg1-3ubuntu2.5); however:
  Package libwinpr2-2:amd64 is not configured yet.

dpkg: error processing package libfreerdp-client2-2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-common (>= 1:7.0.0~alpha~); however:
  Package libreoffice-common is not configured yet.
 libreoffice-calc depends on libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.4); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cryptsetup-bin:
 cryptsetup-bin depends on libcryptsetup12 (>= 2:2.4); however:
  Package libcryptsetup12:amd64 is not configured yet.
 cryptsetup-bin depends on libssh-4 (>= 0.8.0); however:
  Package libssh-4:amd64 is not configured yet.

dpkg: error processing package cryptsetup-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-pro-client-l10n:
 ubuntu-pro-client-l10n depends on ubuntu-pro-client (= 31.2.2~22.04); however:
  Package ubuntu-pro-client is not configured yet.

dpkg: error processing package ubuntu-pro-client-l10n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-driver-550:
 nvidia-driver-550 depends on nvidia-dkms-550 (<= 550.54.15-1); however:
  Package nvidia-dkms-550 is not configured yet.
 nvidia-driver-550 depends on nvidia-dkms-550 (>= 550.54.15); however:
  Package nvidia-dkms-550 is not configured yet.

dpkg: error processing package nvidia-driver-550 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-79-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p1
I: (UUID=62dd32c9-2b5c-4ee8-bed6-50fc8fe0176b)
I: Set the RESUME variable to override this.
Processing triggers for libc-bin (2.35-0ubuntu3.7) ...
Errors were encountered while processing:
 openssh-sftp-server
 tcpdump
 libmysqlclient21:amd64
 mokutil
 openvpn
 grub-efi-amd64-signed
 openssh-server
 bind9-libs:amd64
 openssh-client
 libfreerdp2-2:amd64
 libssl3:i386
 nvidia-dkms-550
 locales
 libwinpr2-2:amd64
 libpython2.7-stdlib:amd64
 tzdata
 apparmor
 transmission-gtk
 libreoffice-common
 python3-cryptography
 nvidia-dkms-530
 libpython3.10-minimal:amd64
 gnome-remote-desktop
 libssh-4:amd64
 libreoffice-gnome
 libreoffice-impress
 libfreerdp-server2-2:amd64
 libpam-systemd:amd64
 libcurl4:amd64
 libcryptsetup12:amd64
 libreoffice-help-en-us
 libkrb5-3:amd64
 libkrb5-3:i386
 language-pack-gnome-en-base
 linux-headers-5.15.0-105-generic
 curl
 python3-uno
 bind9-dnsutils
 python3-paramiko
 bind9-host
 openssl
 libreoffice-ogltrans
 xserver-xorg-legacy
 libreoffice-core
 ubuntu-pro-client
 libfreerdp-client2-2:amd64
 libreoffice-calc
 cryptsetup-bin
 ubuntu-pro-client-l10n
 nvidia-driver-550
Processing was halted because there were too many errors.

```

I also tried other things like:

```
sudo apt -f install
``` and some other commands I found online but to no avail.

Also, trying to install aptitude runs into the dpkg errors.

---

### Post by barko on 2024-04-20
Try this:

```
sudo killall apt
sudo dpkg --configure -a
sudo apt -f install
```

---


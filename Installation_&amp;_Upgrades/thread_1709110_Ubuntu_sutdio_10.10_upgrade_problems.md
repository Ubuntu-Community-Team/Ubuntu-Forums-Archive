---
title: "Ubuntu sutdio 10.10 upgrade problems"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by checoimg on 2011-03-17
W: Failed to fetch [http://do.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011c-0ubuntu0.10.04_all.deb](http://do.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011c-0ubuntu0.10.04_all.deb)
  404  Not Found [IP: 91.189.88.46 80]


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/p/pulseaudio/libpulse-browse0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/p/pulseaudio/pulseaudio-utils_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/p/pulseaudio/pulseaudio_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/p/pulseaudio/libpulse0_0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20100805+b96170a-0ubuntu1_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/main/n/netkit-ftp/ftp_0.17-23_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (20101008)]/pool/universe/b/bluez/bluetooth_4.69-0ubuntu2_all.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/libn/libnice/gstreamer0.10-nice_0.0.12-1_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/universe/f/f-spot/f-spot_0.8.0-1_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20100810t192516.1e6db5a-0ubuntu1_amd64.deb
  Hash Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Studio 10.10 _Maverick Meerkat_ - Release amd64 (2010100]/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20100810t192516.1e6db5a-0ubuntu1_amd64.deb
  Hash Sum mismatch

---

### Post by user1397 on 2011-03-17
it seems like it's trying to upgrade from the cd rom not from the online repositories.  try to comment out the cd rom line from your sources.list file:

```
gksudo gedit /etc/apt/sources.list
```see the line at the top that says cd-rom? put a # in front of it, then save, close, and try 'sudo apt-get update' again

---


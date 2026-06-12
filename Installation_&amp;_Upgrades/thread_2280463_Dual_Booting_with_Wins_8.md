---
title: "Dual Booting with Wins 8"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by leo41 on 2015-05-30
Hi,
  It's been a while since I've been here, but anyways I am trying to dual boot on a windows 8 laptop; unfortunately my laptop's hard drive contains multiple partitions that were created by the laptop's manufacture. Here is a picture of what the partitions look like. As you can see I have already tried to install ubuntu which worked great but I can't seem to installed grub right because grub can't ever find the windows boot partition :(. Please help me, I miss linux...

[https://dl.dropboxusercontent.com/u/77575413/FS.jpg](https://dl.dropboxusercontent.com/u/77575413/FS.jpg) here's that picture!!

---

### Post by ubfan1 on 2015-05-30
This is apparently a UEFI machine, so some things are different, like the boot flag going onto the EFI partition.  Did you install Ubuntu in UEFI mode like Windows?  If not, that probably the reason you have problems.  Secure boot is another UEFI feature which might cause problems -- grub still cannot boot Windows if secure boot is  enabled.  Some reading for you:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---


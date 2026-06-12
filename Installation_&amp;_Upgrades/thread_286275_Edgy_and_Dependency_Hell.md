---
title: "Edgy and Dependency Hell"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Ay Deverrick on 2006-10-27
Last night, right after Edgy came out, I decided to upgrade, since I lvoe having everything as up to date as I can, yet still have a relatively stable system.  Well, I have it download and install as I read in [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) .  Well, some 40 packages didn't install.  I've been playing around with the order that they install with dpkg, and have been having no success due to dependencies.  Apparently all of the packages depend on each other, ergo one can not be installed without the other, but they need x package or something of some sort.

Since I have a wireless internet connection that uses ndiswrapper, and a Nvidia graphics card that requires the special Nividia drivers to work at all in *buntu, I can not do any sort of clean install.  Does anyone know a good order in which to install these packages without forcing an install on one of them?

evms
evms-ncurses
volumeid
initramfs-tools
udev
mdadm
lvm-common
lvm2
pcmciautils
ubuntu-minimal
pcmcia-cs
bluez-pcmcia-support
libgphoto2-2
libgphoto2-2-dev
digikam
f-spot
hal
gnome-power-manager
kubuntu-artwork-splash
kubuntu-desktop
linux-image-2.6.17-10-386
update-notifier
usplash-theme-ubuntu
xsane
ubuntu-desktop

Sorry for the long post, I'd appreciate any sort of help.  I don't wanna use dpkg --force* unless I absolutely have to, for obvious reasons.

[Edit:] After more playing around, I think the core of this problem lies in udev, initramfs-tools and mdadm.  I *think* I might be safe if I force those packages to install regardless of dependencies, and then have the rest install normally.  Thoughts?

---

### Post by TheSqueak on 2006-10-27
I'm having what seems to be a similar problem - my list of failed dependencies is a bit longer than yours though :)

```
Errors were encountered while processing:
 acpid
 acpi-support
 evms
 evms-ncurses
 volumeid
 initramfs-tools
 udev
 mdadm
 lvm-common
 lvm2
 linux-image-2.6.17-10-386
 linux-restricted-modules-2.6.17-10-386
 nvidia-glx
 xserver-xorg
 pcmciautils
 ubuntu-minimal
 libmtp2
 amarok
 pcmcia-cs
 bluez-pcmcia-support
 libgphoto2-2
 libgphoto2-2-dev
 digikam
 digikamimageplugins
 hal
 gnome-volume-manager
 grub
 gthumb
 hwdb-client-common
 hwdb-client-kde
 libipoddevice0
 ipod
 kamera
 kipi-plugins
 libsane
 libkscan1
 kooka
 usplash
 kubuntu-artwork-usplash
 libipoddevice-dev
 linux-image-386
 linux-restricted-modules-386
 linux-386
 sane-utils
 wine
 wine-dev
 xserver-xgl
 linux-wlan-ng
```


Hopefully someone knows how to fix this, i'm not really sure I want to reboot this PC, will it even come back up if I do?

---

### Post by TheSqueak on 2006-10-27
Aha, i've got everything except acpid and acpi-support working.

My problem was that my /boot partition had filled up and I hadn't noticed, d'oh ...

---


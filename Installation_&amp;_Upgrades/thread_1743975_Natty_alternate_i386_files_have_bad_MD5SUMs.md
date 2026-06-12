---
title: "Natty alternate i386 files have bad MD5SUMs"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2011-04-29
The MD5SUM file on the **ubuntu-11.04-alternate-i386.iso **disc is wrong.  It has an incorrect checksum of 2 files and 18 that are missing or have incorrect names.  I'm checking these from a Windows box but that really shouldn't matter.  The two incorrect hashes are:

```
543f56d91223039621db4cf3b50dde37  ./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default
0ae389801f547ccf19bd6f63c0ab3b7d  ./install/netboot/ubuntu-installer/i386/pxelinux.0
```I'm showing an MD5 of D41D8CD98F00B204E9800998ECF8427E for both files...

These are the files which appear to be missing or misnamed (the ones I checked appear to be on the disc but are named incorrectly):

```
./pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12_i386.deb
./pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20110107+b795ca6e-0ubuntu7_i386.deb
./pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2+git20101202.d60087f0-4ubuntu3_i386.deb
./pool/main/l/linux/pcmcia-storage-modules-2.6.38-8-generic-pae-di_2.6.38-8.42_i386.udeb
./pool/main/l/linux/firewire-core-modules-2.6.38-8-generic-pae-di_2.6.38-8.42_i386.udeb
./pool/main/l/linux/fs-secondary-modules-2.6.38-8-generic-pae-di_2.6.38-8.42_i386.udeb
./pool/main/l/linux/storage-core-modules-2.6.38-8-generic-pae-di_2.6.38-8.42_i386.udeb
./pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb
./pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb
./pool/main/p/pulseaudio/pulseaudio-module-bluetooth_0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb
./pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb
./pool/main/p/pulseaudio/libpulse-mainloop-glib0_0.9.22+stable-queue-24-g67d18-0ubuntu3_i386.deb
./pool/main/n/network-manager-pptp/network-manager-pptp_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb
./pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8.1+git.20110207t142407.7e1d989-0ubuntu1_i386.deb
./pool/main/n/network-manager/libnm-glib-vpn1_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb
./pool/main/n/network-manager/network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb
./pool/main/n/network-manager-applet/network-manager-gnome_0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1_i386.deb
./install/netboot/pxelinux.cfg/default
```I have successfully verified the MD5 of the disc image itself, so apparently this is the real deal... However despite having 20 errors, if I actually boot a virtual machine to the disc image and verify the integrity from the install menu, it passes.  If I mount the same image in Windows or check them on the burned disc, I have the same results on two different machines using two different hashing programs.  Can anyone confirm that these are bad?

---

### Post by Karl1982 on 2011-04-30
Anyone?

---


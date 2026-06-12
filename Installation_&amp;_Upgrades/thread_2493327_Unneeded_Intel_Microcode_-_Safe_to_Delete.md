---
title: "Unneeded Intel Microcode - Safe to Delete?"
date: 2023-12-11
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2023-12-11
In searching it seems all reference no WiFi available. Maybe this is unique? Here is my delima ...

I have an AMD CPU, and UbuntuStudio v20.04 ... but Update wants to install/upgrade "intel-microcode" pkg. 
In looking in Synaptic I see it and "amd64-microcode" and selecting the intel version it shows;

To Be Removed:
 Linux-image-lowlatency-hwe-20.04
 Linux-lowlatency-hwe-20.04

To Be Installed:
 linux-image-5.15.0-89-lowlatency
 linux-modules-5.15.0-89-lowlatency

Is this Safe? Isn't that already installed? 
<CODE>
uname -srm
Linux 5.15.0-88-lowlatency x86_64
</CODE>

Unsure whether to Remove the un-needed Intel Microcode???
Thanks!

---

### Post by #&amp;thj^% on 2023-12-11
It is a dependency on the kernel, AMD CPU here as well
```
apt depends linux-image-generic
linux-image-generic
  Depends: linux-image-6.5.0-9-generic
  Depends: linux-modules-extra-6.5.0-9-generic
  Depends: linux-firmware
  Depends: intel-microcode
  Depends: amd64-microcode
  Recommends: thermald

```
Both intel and AMD microcodes are now dependencies of the Linux kernel.
And it reads 
```
apt show intel-microcode amd64-microcode
Package: intel-microcode
Version: 3.20231114.1
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Henrique de Moraes Holschuh <hmh@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 12.5 MB
Depends: iucode-tool (>= 1.0)
Recommends: initramfs-tools (>= 0.113~)
Conflicts: microcode.ctl (<< 0.18~0)
Homepage: https://github.com/intel/Intel-Linux-Processor-Microcode-Data-Files
Task: cloud-minimal
Download-Size: 6,051 kB
APT-Manual-Installed: no
APT-Sources: http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
Description: Processor microcode firmware for Intel CPUs
 This package contains updated system processor microcode for
 Intel i686 and Intel X86-64 processors.  Intel releases microcode
 updates to correct processor behavior as documented in the
 respective processor specification updates.
 .
 For AMD processors, please refer to the amd64-microcode package.

Package: amd64-microcode
Version: 3.20231019.1ubuntu1
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Henrique de Moraes Holschuh <hmh@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 381 kB
Recommends: initramfs-tools (>= 0.113~) | dracut (>= 044) | tiny-initramfs
Breaks: intel-microcode (<< 2), linux-firmware (<< 20220819.git8413c63c-0ubuntu1~)
Replaces: linux-firmware (<< 20220819.git8413c63c-0ubuntu1~)
Task: cloud-minimal
Download-Size: 172 kB
APT-Manual-Installed: no
APT-Sources: http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
Description: Processor microcode firmware for AMD CPUs
 This package contains microcode patches for all AMD AMD64
 processors.  AMD releases microcode patches to correct
 processor behavior as documented in the respective processor
 revision guides.  This package includes both AMD CPU microcode
 patches and AMD SEV firmware updates.
 .
 For Intel processors, please refer to the intel-microcode package.


```
```
apt policy intel-microcode amd64-microcode
intel-microcode:
  Installed: 3.20231114.1
  Candidate: 3.20231114.1
  Version table:
 *** 3.20231114.1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
amd64-microcode:
  Installed: 3.20231019.1ubuntu1
  Candidate: 3.20231019.1ubuntu1
  Version table:
 *** 3.20231019.1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```
For a dry run removal:
```
sudo apt remove intel-microcode -s
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode gjs libgjs0g libmozjs-115-0 libpkcs11-helper1 linux-headers-generic
  network-manager-openvpn openvpn thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  intel-microcode linux-generic linux-image-generic surfshark
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv linux-generic [6.5.0.9.11]
Remv surfshark [1.7.3-2256]
Remv linux-image-generic [6.5.0.9.11]
Remv intel-microcode [3.20231114.1]

```
So you see it not safe to remove.

---

### Post by The Cog on 2023-12-11
I don't see any reason why you should want to remove it anyway, just because you don't think you will need it. Same goes for your appendix. 
Ubuntu is intended to be fairly general-purpose, which means the default installation pulls in a lot of things that not everyone will need but some users will need. You could spend years removing things that are installed that you don't think you need, and reinstalling when you get it wrong. My advice is to not bother - go with the flow and spend your time on more productive (and interesting) things. It's a different thing if some packages are actually causing problems though, but that's really unusual.

I think Ubuntu has an Ubuntu-minimal installer that just installs the bare minimum to be usable if you prefer. Than's not my idea of a fun time so I've never looked at it though, and can't comment on it.

---

### Post by grahammechanical on 2023-12-12
In the past microcode used to be installed through Software and Updates>Additional drivers tab. Now it is installed automatically. I understand that microcode updates the BIOS code every time the OS is booted. It removes the need for the user to do a BIOS upgrade which can go wrong and make the motherboard unusable. I do not think that microcode is for the CPU directly but for the motherboard to make it compatible with newer hardware that the user may install.

Let us not forget that the x86 motherboards we are using are an Intel development. AMD produced a 64 bit CPU before Intel but it was (had to be) compatible with the Intel code. Could this be why a motherboard with an AMD CPU needs both an Intel and a AMD type of microcode? Ubuntu would not install it if it was not needed in some way.

Regards

---

### Post by Rick St. George on 2023-12-13
I suppose its not worth the time and trouble. Such as I don't have Bluetooth on my Desktop computer, but if I try to Remove it, it wants to remove a lot of programs I need and use but does not use bluetooth .... Go Figure ?!?!?  Same with Avahi, etc.

---


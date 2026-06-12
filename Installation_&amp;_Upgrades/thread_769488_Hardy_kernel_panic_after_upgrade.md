---
title: "Hardy kernel panic after upgrade"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by karaluh on 2008-04-26
I've got a problem with the new kernel. After upgrade Gutsy->Hardy which went fine reboot welcomes me with Kernel panic - not syncing: VFS: unable to mount root on unknown-block(0,0). Trying to boot Gutsy kernel ends in BusyBox. Quick look around in it showed no hard drive devices (sda/sdb/hdc/hdd in /dev). I did boot with System Rescue CD, mounted /boot and rolled back initrd to the one generated during gutsy install for 2.6.22. I successfully booted Gutsy kernel then. update-initramfs successfully actualized initrd for 2.6.22 so there has to be some problem with the kernel. I've tried to reinstall it, install 2.6.22-16-386, server and pci=nomsi option with kernel panic everytime. Ubuntu Live CD recognizes all drives correctly, but overwriting 2.6.24 kernel with the one from Live CD doesn't help. I've got lvm on software raid, but that shouldn't matter here. System installed on sata drives, and besides those two, I've got one hdd and dvd-rw on pata. Chipset is nforce2, sata controller PDC20376, Any ideas?

---

### Post by Solrac924 on 2008-04-26
do all files exist in /boot:
abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic

---

### Post by karaluh on 2008-04-27
> **Solrac924 said:**
> do all files exist in /boot:
abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic

Thanks for your reply. Yes, all the files are in place. I also recompiled Hardy kernel, without luck.

---

### Post by mgazb on 2008-05-01
I get the same problem after upgrading from 7.04 through 7.10 to 8.04.

Kernel panic not syncing VFS Unable to mount root fs on unknown block

The grub menu lists 

2.6.24-16 generic
2.6.24-16 generic (recovery)
2.6.22-14 generic
2.6.22-14 generic (recovery)
2.6.20-15 generic
2.6.20-15 generic (recovery)

I can boot into the 2.6.20-15 kernel but each of the others produce the kernel panic.
How do I get the new kernel booting?

---

### Post by garton on 2008-05-02
I have this exact same problem. Gutsy kernel works fine, Hardy kernel panics. I have a Ubuntu Server installation. No idea what's wrong. Will follow this thread.

---

### Post by garton on 2008-05-02
I have also tried adding:

noapic nolapic noacpi acpi=off

... to the boot command. This did not have any effect at all.

---

### Post by FishRCynic on 2008-05-02
try disabling or removing any cpu scaling util/daemon and see if it boots

ie uninstall powernowd, cpufreq etc.

i have one x64 machine that this will allow it to boot and a
nvidia fix turning off the power saving on the gpu that stops it
from a hard lockup
(amd 5000 x t5070 mb)

[i am not at that machine presently but approx 12-15 hours from now i will
try to edit this with the links to the appropriate posts i gleaned the info from.]

---

### Post by Solrac924 on 2008-05-03
well, my GRUB also shows 2 kernals with 8.04: 24-16 & 22-14. i did get a panic lock-up with 24-16 once, but now it boots each & every time. what i did was boot using 22-14, & get all updates. :-?

---

### Post by ShelJ on 2008-05-03
> **garton said:**
> I have this exact same problem. Gutsy kernel works fine, Hardy kernel panics. I have a Ubuntu Server installation. No idea what's wrong. Will follow this thread.

I'm getting the same problem.  I can trace it back to my update last night where I got the following messages during SPM's upgrade process:

```
E: linux-ubuntu-modules-2.6.24-17-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-17-server: subprocess post-removal script returned error exit status 1
```

Since then i kept getting this message, and I cannot unmark those or anything related to 2.6.24-17 from my install/remove listing, and cannot add/remove anything through SPM as the process gets stuck on this issue!!  I tried removing these through terminal an here is the out put for that:
```
sudo apt-get remove linux-ubuntu-modules-2.6.24-17-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-17-generic linux-ubuntu-modules-2.6.24-17-server
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 35.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 255804 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-17-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-17-server ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-server

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-server
dpkg: error processing linux-ubuntu-modules-2.6.24-17-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am able to load kernel 2.6.24-16, however, fine.

Sorry for the long post, I hope that some one can help if I give as much information as I can.

---

### Post by Solrac924 on 2008-05-06
you know what, my 24-16 kernal loads up about half the time. it's just hit & miss. the 22-14 is always reliable & boots up all the way everytime. :?

---

### Post by jcolley on 2008-05-13
same issues here 22 works every time 24 hit os miss

---


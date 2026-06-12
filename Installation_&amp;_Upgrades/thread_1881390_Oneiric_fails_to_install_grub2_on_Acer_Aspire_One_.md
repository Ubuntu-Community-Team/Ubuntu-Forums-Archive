---
title: "Oneiric fails to install grub2 on Acer Aspire One ZG50"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by codfish45 on 2011-11-15
Can't find anything on this exact problem...

I'm trying to install Ubuntu 11.10 32 biton an Acer AspireOne ZG50 netbook (8gB ssd , 1.6ghz atom processor, factory BIOS) from USB.  Install is normal, but at the end it says that grub failed to install and gives me the option to install to sda or sda1.  With either option the install completes, and the computer is unbootable at startup.

Logical next step was to try manually installing grub via liveUSB.  fdisk -l returns sda1, sda2, and sda3 for the machine hd, + sdb1 for the USB.  boot-repair doesn't help with default repair or fixing MBR, and option for grub installation is not available.

I then tried mounting sda1 to /mnt and entering
 ```
sudo grub-install --root-directory=/mnt /dev/sda1
```
which attempts to run and returns that it cannot write to /dev/sda1

I also tried 
```
sudo grub
```
which returned as an unkown command.

I have tried redownloading Oneiric installer with no luck.  I have yet to try other distros or Ubuntu versions or flashing the BIOS.  I do know that Ubuntu 10.04 netbook remix had previously been installed on this computer, so it must be possible to install it, but I'm kind of boggled at this point.  Any thoughts??

---

### Post by oldfred on 2011-11-15
You should be installing to sda not sda1.

Grub 1.99 not uses boot not root, but the old command is supposed to work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda
[/COLOR]
If that does not work post the link from boot repair to Boot Info Script.

---

### Post by codfish45 on 2011-11-15
Thanks, but that didn't work.  Same errors come up.
Here is the boot-repair output:
[http://paste.ubuntu.com/739865/](http://paste.ubuntu.com/739865/)
Flashed the BIOS and changed the disk boot priority on the off chance that it would help matters, but no dice.  :(

---

### Post by oldfred on 2011-11-16
You have no grub.cfg file which is the boot menu. And it never installed grub2's bootloader to the MBR as you still have syslinux in the MBR. It is as if grub is mostly missing. 

You could chroot into system & reinstall grub or reinstall making sure to install grub to the MBR of the drive you install to. Some systems may promote a drive to sda or it may be sdb.

Since it looks like all of Ubuntu is there, you may be able to boot with this and then reinstall grub2 from command line once booted.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---


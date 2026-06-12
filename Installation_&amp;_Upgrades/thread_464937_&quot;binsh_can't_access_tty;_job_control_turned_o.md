---
title: "&quot;/bin/sh: can't access tty; job control turned off&quot; cause still unknown :("
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by bdmp on 2007-06-05
Here is the story of my upgrade to fiesty. It is not working currently after about a month.

Here is what happens when I boot one of the two kernels:

1.

2.6.17-11-generic
Begin: Waiting for roof file system...

Then it just sits there untill eventually,
/bin/sh: can't access tty; job control turned off
(initramfs)

2.

2.6.17-10-generic
Mounting local file system... [fail]
Activating swapfile swap...  [OK]

and then it just hangs...


This "/bin/sh: can't access tty; job control turned off" seems to have many causes and I have not been able to figure out what mine is yet. Any help would be appreciated

---

### Post by dabl on 2007-06-05
This error seems to happen when a kernel upgrade results in a mis-match between the "alleged" location of the root directory "/" in /boot/grub/menu.lst and the "actual" location of the boot partition as listed in /etc/fstab.  

Print out your menu.lst file and compare it carefully to fstab, and then edit menu.lst to make the root directory match the root partition information in fstab.  They have to be the same, and fstab is the expert on where things are, partition-wise.

HTH

---

### Post by bdmp on 2007-06-05
Thank you. Am I missing what is different in these files?

fstab;
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=85b1eb3c-8f01-4478-9b58-3ae813807ae8 /               ext3    defaults,errors=remount-ro,usrquota,grpquota
0       1
# /dev/hdc5
UUID=2e76ec60-1ca0-4f82-a73d-7fe14699a1ea none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and menu.lst
```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

```

---

### Post by dabl on 2007-06-05
How did the first hard drive (hd0) get to be identified in fstab as hdc?  Are there more hard drives in your system -- have you changed the drive boot sequence in your BIOS?  It looks like fstab thinks it is the third hard drive, but menu.lst thinks it is on the first one.

---

### Post by bdmp on 2007-06-05
There are no other drives in the machine. I was using the drive as a second drive in another machine and I moved it in to this one and it showed up as hdc. I never had a problem with it so I just left it.

So what do I do?

Thanks.

---

### Post by dabl on 2007-06-05
The other item of concern is the use of UUID numbers in fstab, but not in the menu.lst.  Starting with Feisty, I have the impression that the (K)Ubuntu system is relying more on the UUID system than the old "hdx/sdx" system for drive identification for all kinds of drives.  Mine has the drives ID's by UUID in both menu.lst and fstab.  However, some folks prefer to comment out the UUID number, and un-comment the /dev/hdx designator for their hard disks, on the theory that the older method is more reliable.

I'm not sure what will fix your situation.  Since it's non-functional as-is, I guess you might trying making a backup copy of both fstab and menu.lst, and then manually edit them to show the root directory being on /dev/hda1, (i.e. change it from hdc1 to hda1), and comment out the UUID number in fstab, and un-comment the /dev/hda1.  

I'll cross my fingers ....

:)

---

### Post by bdmp on 2007-06-05
You said...

"manually edit them to show the root directory being on /dev/hda1, (i.e. change it from hdc1 to hda1)"

but my root is hdc1, so I want fstab to say that right? Is there a way to change the name of my partition? Do you follow?

---

### Post by dabl on 2007-06-05
Well, that's part of what is puzzling in your setup.  I copied this from a Google search:

> All hard disk drives in the Linux operation system have special names, which consist of three parts, two of which are listed here:

    * Two symbols "hd" or "sd" for the IDE and SCSI disk drives
    * One symbol somewhere in the range from "a" to "h" for the IDE disk drives, or the range from "a" to "p" for SCSI ones. 

(I have to mention that for different Linux distributions, this range could differ. For example, Red Hat Linux 7.2 uses the range "a" to "l" for the IDE disk drives, and a range from "a" to "az" (two symbol combination!) for the SCSI drives).

This second symbol defines the number of device. SCSI disk drives use sorted numbering, which depends on the ID of device. The IDE scheme differs a bit. Let's
look at the scheme:

    * a and b - Master and Slave disks at the Primary interface of the 1st IDE controller
    * c and d - Master and Slave disks at the Secondary interface of the 1st IDE controller
    * e and f - Master and Slave disks at the Primary interface of the 2nd IDE controller
    * g and h - Master and Slave disks at the Secondary interface of the 2nd IDE controller 

...and so on.

So, if your hard drive is the only one connected to your IDE controller, unless you deliberately set it as a "second IDE device", it should be recognized as hda, NOT hdc.  And the Grub loader is correctly naming it hd0,0, meaning the first partition on the first hard drive.  So, something seems to be amiss in your IDE setup, or your BIOS, regarding how this drive is identified and sequenced in the boot device ordering.

:(

I also see that your fstab names the CD ROM drive as hda.  That may be relevant to your problem.  Here's an experiment you could try -- change the CD ROM to hdb, and your hard drive to hda, and reboot that way.

---


---
title: "/dev/hda4 does not exist!"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by smartsaga on 2005-10-16
Hi there,

I just installed Ubunto 5.10 on my system. I have windows XP running on my machine with the following:

4 x 120GB HD
1 x 200GB HD
1 x CD-RW/DVD combo
1 x DVD-RW +-

I have a built in IDE controller and an extra one. The boot device is set to SCSI to allow the extra IDE card to be the one to boot. I did thid because the HDs on the PCI-IDE controller are marked as the first drives in the system and because the HD that's there is the one that has Windows XP and Ubuntu (hda or hd0 in grub's terms)

The problem:

After installing Ubunto (everthing there was fine) the system started to boot and I got a grub boot menu. I then selected Ubuntu, kernel 2.6... and everything seemed fine. It loads the kernel and shows the splash screen that says Ubuntu, has a progress bar and at the bottom says Loading modules. Then it stops and says:

...
Uncompressing Linux... Ok, booting the kernel. 
Loading, please wait
Alert! /dev/hda4 does not exist. Dropping to a shell!

Any ideas of what happened?

I repeated the install process several times and I get the same results.

Disk 1 (hda) has the following partitions 4 Primary:

hda1 - 29Gb FAT 32 (windows XP)
hda2 - 9GB FAT 32 (empty - used for data)
hda3 - 2GB SWAP (err... SWAP)
hda4 - 70+GB Reiserfs or Ext3 (where SUSE 10 was, now obsolete Ubuntu)

EDIT: I formatted hda4 in the installation, once with Ext3 and afew times with Reiserfs , just in case anybody wonders. /EDIT

Please note that I have installed many other Linux distros on this PC. Just before installing Ubuntu I had SUSE 10 in the partition /dev/hda4/ and it worked fine. I installed SUSE 10 just to make sure I wasnt doing anything wrong with Ubuntu. It would suck if I cannot run Ubuntu!!!

Thank you for reading.

---

### Post by adwait on 2005-10-16
Wierd....try the command
```
sudo fdisk -l
```
Does it list that partition?

---

### Post by smartsaga on 2005-10-16
Seems like the PCI IDE controller had an option for Windows 2000. I just pushed the stupid button and then it worked just fine.

Now, I just hope that doesn't mess up all my other stuff.

I don't know why all the other distros got thrugh that part just fine. I mean, they all had GRUB as the boot loader...

---

### Post by smartsaga on 2005-10-16
I just rebooted after installing the ATI drivers...

Ubuntu failed to boot again... Now that everything was running just fine. :( 

It seems that I have to hit F1 on the controller screen each time I want to run Ubuntu. :confused: 

Have a good one.

---

### Post by beefsprocket on 2005-10-17
Same problem here with /dev/hda1 instead. I created a thread previous to finding this one.
[http://ubuntuforums.org/showthread.php?p=419772&posted=1]("http://ubuntuforums.org/showthread.php?p=419772&posted=1")

I've yet to try reiserfs. Sounds like it won't make a difference.

---

### Post by smartsaga on 2005-10-21
[QUOTE=adwait]Wierd....try the command
```
sudo fdisk -l
```
Does it list that partition?[/QUOTE]
Following the suggestion of adwait:
===============================
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/hda2            3825        5101    10257502+   c  W95 FAT32 (LBA)
/dev/hda3            5102        5363     2104515   82  Linux swap / Solaris
/dev/hda4            5364       14946    76975447+  83  Linux
===========================

Now, becuase I have an extra PCI IDE controller I have to hit F1 whenever I want to boot Ubuntu. The controller says: "Press F1 or F11 for Windows 2000" and whenever I press F1 Ubuntu boots just fine.

When I installed SUSE 10 there were no problems with GRUB saying that the partition /dev/hda4 did not exist. Is this a bug in the installer?

Is there a graphical tool to easily setup Grub?

---


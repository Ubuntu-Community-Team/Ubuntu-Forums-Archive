---
title: "MBR Problem-- Windows Installed Over Ubuntu"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by pcpete on 2007-08-13
Hello, I realize this has been discussed on the forum before... but I am without an answer. I had a tricked out Ubuntu box dual booting with Windows, but I tried reinstalling windows knowing it would overwrite the MBR. Now, my system will not boot and the filesystem is in sorts :( 

Here's my current filesystem: 

#fdisk -l 
-------------------------------------------------------------------------------
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       10199    81915435    f  W95 Ext'd (LBA)
/dev/sda2   *       10200       25496   122873152+   b  W95 FAT32
/dev/sda3           25497       38791   106792087+  83  Linux
/dev/sda4           38792       38913      979965   82  Linux swap / Solaris
/dev/sda5               2       10199    81915403+   7  HPFS/NTFS
--------------------------------------------------------------------------------

I tired changing the boot flag with fdisk and also tried Grub-install /dev/sda. These were great tutorials I played with, and it just so happens I ran DD to backup the first sector (512bytes) of the drive to restore MBR... 

Windows has yet to go into reinstall STAGE 2, but it looks like my system is now shot.. Any ideas? 

I gave these tuts a shot: [http://www.andrejciho.com/category/linux/](http://www.andrejciho.com/category/linux/)

---

### Post by pcpete on 2007-08-13
I was successful in re-writing MBR with DD, but since I did a FULL format with windows it does not boot ... damn i think i am screwed

---

### Post by Shazaam on 2007-08-13
Are you saying just Windows won't boot or the whole system? Here is a good page that might help....
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by pcpete on 2007-08-13
Whole system, I am getting that dreaded "Invalid System Disk" error. I'll check out that link, thanks!


>>Windows has not been installed yet, so after a fresh Windows install there is still an MBR error. This seems like a permanent file table problem.

---

### Post by logos34 on 2007-08-13
Boot from the live cd and try reinstalling grub again.

[B]sudo grub
> find /boot/grub/stage1[/B]
(should show 'hd0,2'--enter in next command)
[B]> root (hd0,2)
> setup (hd0)[/B]
> quit

Check that your hard disk settings in the bios are correct, and try setting the hard disk to first boot position, followed by cdrom.

---

### Post by Erlander on 2007-09-11
Logos34,

Thank you.

My Windows install was very sluggish so I re-installed and thanks to you Ubuntu also now works.

:guitar::guitar:

Rob

---


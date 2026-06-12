---
title: "Fresh Install Grub Problems!"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by mattpark on 2006-09-08
Hi people. 

After Getting Ubuntu to work nice and dandy on my Sony Vaio SZ1XP, with dual boot i decided it was time to set my desktop up with dual boot. 

Ran the install from live cd, all went swimmingly. Reboot. Grub menu comes up fine. "Error 17". Posts the same for my XP install too "Error 17"

Find it odd since i didn't set up and partitions myself etc, just let the installer take care of it. 

I have four sata disks installed on my system. 

sda - 250gb drive - XP Installed
sdb - 200gb drive - 1 single NTFS partition used to store media. 
sdc - 80gb drive - 1 single NTFS partiton with my music on. 
sdd - 80gb drive - Empty/clear space. (I told the ubuntu installer to use the largest clear space to install on, so i'm assuming it will be setup here with the appropriate partitions)

Just to confirm, i booted up the live cd and checked how it had partitioned the drive:

/dev/sdd1 - ext3 - 73.21gb - flags "boot"
/dev/sdd2 - extended - 3.12gb
/dev/sdd5 - linux-swap - 3.12gb


So, that's how i have my drives setup as. I tried a guide on how to reinstall grub to the letter, but on reboot i have exactly the same problem. 

A little guidance on how to fix my issue would be greatly appreciated!

Thanks

Matt :-k

---

### Post by zxee on 2006-09-08
Sata drives can have some odd issues IMO.
Perhaps looking at or posting your /boot/grub/menu.lst and the output of fdisk -l will get us somewhere.

---

### Post by mattpark on 2006-09-08
Hi zxee. 

Output of sudo fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9557    76766571   83  Linux
/dev/sdd2            9558        9964     3269227+   5  Extended
/dev/sdd5            9558        9964     3269196   82  Linux swap / Solaris



and content of /boot/grub/menu.lst .... you'll have to bear with me on that one. Be with in in 2mins!

lol

---

### Post by mattpark on 2006-09-08
okay, how do i look at that from the live cd?

At the moment im using 

sudo vi /boot/grub/menu.lst

... and no file is there so vi creates a new one?

---

### Post by mattpark on 2006-09-08
Please peeps, really need to get this fixed before i head out! Stumped at the moment!

Help!:confused:

---

### Post by confused57 on 2006-09-08
You might want to check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=253031](http://www.ubuntuforums.org/showthread.php?t=253031)

SATA drives can definitely present some problems with grub...you might want to try highlighting the Ubuntu entry in the grub menu, then press "e" for edit, and try some different root combinations, e.g. root (hd3,0), root (hd0,0), etc...you'd probably need to change the dev in the kernel line to point to the same hd & partition...(hd3,0) = sdd1, (hd0,0) = sda1, etc. and you may be able to get Ubuntu to boot, if you happen on the correct root partition as recognized by grub.  This is only a temporary change, if you get Ubuntu to boot, you'd need to make the change permanent in /boot/grub/menu.lst.  I'm sure there is a much easier way, but you may want to play around with it.

---

### Post by zxee on 2006-09-08
> **mattpark said:**
> Please peeps, really need to get this fixed before i head out! Stumped at the moment!

Help!:confused:

The file /boot/grub/menu.lst The letter before the s in menu.lst is a lower case L. If you don't have a menu.lst something is wrong.

Added later: There is documentation here: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)  I'll be away myself for a few days so I hope you can get it working from the guides-or other helpers.

---


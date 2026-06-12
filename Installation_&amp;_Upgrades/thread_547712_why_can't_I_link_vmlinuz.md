---
title: "why can't I link vmlinuz?"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by saphil on 2007-09-10
sudo ln -s /boot/initrd.img /home/initrd.img creates a link where I want it but it is a broken link.    

Why do I want to do that? my home directory in in the 1st hdd and the rest of the OS is in the slave drive  

Why is that? the order used to be reversed, but the home dirs needed more space. 

 Am I just going to have to get a screwdriver and reverse the order of the drives on the cable?

---

### Post by logos34 on 2007-09-10
sounds like you just need to edit fstab and menu.lst, and/or reinstall grub.  Forget the symbolic link stuff.  Post your fdisk

**sudo fdisk -l **(lowercase L)

---

### Post by saphil on 2007-09-11
Disk /dev/hda: 30.0 GB, 30020272128 bytes <br>
255 heads, 63 sectors/track, 3649 cylinders<br>
Units = cylinders of 16065 * 512 = 8225280 bytes<br>
<br>
   Device Boot      Start         End      Blocks   Id  System<br>
/dev/hda1               1        3649    29310561   83  Linux<br>
<br>
Disk /dev/hdd: 20.5 GB, 20520493056 bytes<br>
255 heads, 63 sectors/track, 2494 cylinders<br>
Units = cylinders of 16065 * 512 = 8225280 bytes<br>
<br>
   Device Boot      Start         End      Blocks   Id  System<br>
/dev/hdd1   *         383        2494    16964640   83  Linux<br>
/dev/hdd2               1         382     3068383+  82  Linux<br> swap / Solaris<br><br>

---

### Post by logos34 on 2007-09-11
> Am I just going to have to get a screwdriver and reverse the order of the drives on the cable?

Actually they're on separate cables--hda is master on the primary IDE channel (IDE0), and hdd is slave on the secondary IDE channel (IDE1).  Your cdrom is probably master on that channel.

Sounds like you're booting to grub on hda, which points to root partition on hdd (grub installs by default to the first Bios hard disk despite the fact that ubuntu is elsewhere).  But root is still looking for /home on the hdd disk.   

Go into your Bios at startup and double check that the hda drive is ahead of hdd in the hard disk boot order. Then Boot the ubuntu live cd, open a terminal and type these commands:

[B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdd1 /mnt/ubuntu 
gksudo gedit /mnt/ubuntu/etc/fstab[/B]

Change the home entry to this:

> /dev/hda1 /home ext3 defaults 0 2

Then,

**gksudo gedit /mnt/ubuntu/boot/grub/menu.lst**

All 'root' lines should point to **(hd1,0)**.  Also,check 'groot' line near top.

/mnt/ubuntu/boot/grub/device.map should read:

> (hd0) /dev/hda
(hd1) /dev/hdd

Reinstall grub:

[B]sudo grub
find /boot/grub/stage1 [/B] -->it should output '(hd1,0)'
[B]root (hd1,0)
setup (hd0)
quit[/B]

Try that.

---

### Post by saphil on 2007-09-11
thanks, I have done that (even made sure that _all_ the fstab files showed the same thing)  The result was not a success.  I can still jumpstart the machine using the live-disc and choosing "boot from first hard drive"

---


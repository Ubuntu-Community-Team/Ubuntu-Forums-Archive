---
title: "updating = KO?"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by pippopappo on 2007-07-03
Hi everyone,

I'm in a big trouble.

I've installed Ubuntu 7.04 on my PC in a dual boot configuration. Windows on the primary master disk, Ubuntu on the primary slave disk, with Windows boot loader (during installation I've installed grub on a floppy and then I've put it on Windows). For some days everything worked OK: if I boot form disk (primary master) the Windows boot loader starts and I can choose between Windows and Ubuntu, if I boot form floppy grub starts and I can choose between Ubuntu and Windows.
Yesterday I made the updates Ubuntu told me: when I resterted the PC grub doesn't start: if I boot from floppy (but even if I choose Ubuntu from Windows boot loader when I boot from the primary master disk), I get a blank screen with a "GRUB" string written on the top: I can do nothing but restart PC. Fortunately Windows can start...

Is there someone can help me?

Many thanks

Pippo

---

### Post by Pumalite on 2007-07-03
One of two things: the update changed your menu.lst or corrupted your GRUB. In the first place check your menu.lst and see if it makes sense. If you have a backup, compare it. If Grub is corrupted you might need this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

---

### Post by pippopappo on 2007-07-03
Hi,

I found some differences in menu.lst file

Old menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


New menu.lst

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

The update process has modified the kernel from 2.6.20-15 to 2.6.20-16

What can I do now?

Pippo

---

### Post by Pumalite on 2007-07-03
Do you still have the 15-generic in your Grub?

---

### Post by pippopappo on 2007-07-03
Yes, I have both the 15-generic and 16-generic in /boot.

---

### Post by Pumalite on 2007-07-03
Post your /etc/fstab.

---

### Post by pippopappo on 2007-07-04
Hi,

Here is the /etc/fstab content:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ce9ef31b-7163-41cb-ae75-1cb791045ddd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=41135a0a-ff63-4ca5-9473-712877a457de none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Do you see any problem?

Pippo

---

### Post by Pumalite on 2007-07-04
I cannot say that I do. Maybe someone more knowledgeable will jump in.

---


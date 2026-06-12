---
title: "Error 17: Cannot mount selected partition"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Depressed Man on 2007-06-24
Argh..so I uninstalled Wubi in Windows Vista, resized the Vista partition to give Linux 15 GBs of space. I allocated 3 GBs of it to swap (I have 2 GBs of RAM in my laptop but I read that hibernate/suspend works better with more swap ram) so that's 12 GBs for the ext3 file system which I gave it the bootable flag. Installed Ubuntu with Grub so it shows the listings, I can get into Vista just fine. However, I can't get into Linux.

I only have one built in HDD. But it has probably 4 partitions now, Vista, Vista's recovery, (those two came on my laptop), then ext3 and swap. I'm pretty sure I set ext3 to bootable and primary while swap is extended.

So what's wrong? I'm using Super Grub now (had to use it to fix error 17 that wouldn't bring me to the screen that lets me choose the OS).

---

### Post by Pumalite on 2007-06-24
You have to edit menu.list and add Vista.

---

### Post by Depressed Man on 2007-06-24
Vista is showing up and working. It's Linux that's the problem :(

---

### Post by Pumalite on 2007-06-24
Then try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Depressed Man on 2007-06-24
Ah I'm sorry, I forgot what I meant to say. (was wondering why you kept directing me to pages dealing with how to get to the menu.lst)  Supergrub fixed the problem so I can get to the listings of the OSes. So that's no longer an issue. My problem is that when grub loads it shows

Ubuntu Kernal whatever
Ubuntu kernal whatever (recovery)
Ubuntu memtest

Windows Vista

What I want to know how to fix is loading Linux. From these boot options I can choose Vista (and enter it) but if I choose Ubuntu I get error 17 cannot mount partition.

---

### Post by confused57 on 2007-06-24
> **Depressed Man said:**
> Ah I'm sorry, I forgot what I meant to say. (was wondering why you kept directing me to pages dealing with how to get to the menu.lst)  Supergrub fixed the problem so I can get to the listings of the OSes. So that's no longer an issue. My problem is that when grub loads it shows

Ubuntu Kernal whatever
Ubuntu kernal whatever (recovery)
Ubuntu memtest

Windows Vista

What I want to know how to fix is loading Linux. From these boot options I can choose Vista (and enter it) but if I choose Ubuntu I get error 17 cannot mount partition.

Boot into Ubuntu with SGD, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

then post the output of:
```
gedit /boot/grub/menu.lst
gedit /etc/fstab
```
for your menu.lst, you just need to post the entries to boot Ubuntu

Another you might do is run this command:
```
blkid
```
this will show the current UUID's of your partitions, compare this output with the UUID's in your menu.lst and fstab

---


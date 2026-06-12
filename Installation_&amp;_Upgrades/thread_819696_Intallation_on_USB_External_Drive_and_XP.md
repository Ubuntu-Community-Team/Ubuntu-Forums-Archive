---
title: "Intallation on USB External Drive and XP"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by augusto.sisa on 2008-06-05
Hello,

Recently,  I had install successfully Ubuntu 8.04 in a  USB External HD (300GB) with four partitions as this:

1. 50GB /
2. 100GB /home
3. 2GB swap 
4. rest in fat32 fr share files with windows XP

My laptop is a DELL latitude D300, and the internal HD has a partition NTFS with XP without problems. During the installation process I set the BIOS to boot from the USB, and install GRUB in the MBR of the external disk on /dev/sda so I just can start Ubuntu  when the external HD is plugged to the laptop otherwise it start XP.

The problem that  have is that after the instalation XP can get access to the external HD. I can't see any partition even the FAT. I can't see the disk on disk manager of XP or in system information or on any place. But it's enabled to load the Ubuntu.

So I'm looking to some help about what I need to change and how to change the external HD so I can read it since XP and from Ubuntu.

Thanks.


Augusto

---

### Post by n6yga on 2008-06-05
Did you install GRUB to the MBR of the USB drive? What happens when you select the USB drive to boot from? Tell me more as I think I have the answer for you, but I need more info.

Mark.

EDIT: Ok, I re-read your post. It seems you DID install GRUB to the MBR of th e USB drive. Good. However, while GRUB is perhaps the most intelligent, and most versatile boot manager, it can, at times, be rather dumb. I would be willing to bet that it thinks that you would be booting Ubuntu RELATIVE to your first hard drive. This is UNTRUE in your case because you are telling the machine to boot the USB drive as HD0!! I went through this a while back with multiple-distros installed on an external USB hard drive. Fortunately, the fix is easy!

Grab a liveCD, boot it, mount the USB hard drive. Then, as root, find: /boot/grub/menu.lst on your USB hard drive. Edit this file as root with nano, or gedit, or whatever. Find the line that says: #groot=??? ((hd1, 0) or whatever. Change this to #groot=(hd0,0). 

Also, look at your kernel lines for 'root=/dev/sda1' or something like that. Remember what it says.

Save your menu.lst file.

Edit as root: /boot/grub/device.map file. it will have a couple of lines in it that look something like: '(hd0) /dev/sda. You want to make sure that your USB drive is mapped to (hd0). Your internal drive can be: (hd1) /dev/sdb, or whatever.

This is required because GRUB doesn't realize that you are using the bios to boot it.

I hope this helps. If you have more problems, please ask here. I will try and follow this thread.

---

### Post by logos34 on 2008-06-05
wait, what's the problem?  Is it that you can't boot ubuntu, or cannot access/see ubuntu files from XP?

If even the fat32 partition doesn't show in XP disk management, that's odd.  At a minimum XP usually sees linux partitions as 
'unknown' type, but it detects them nevertheless.  You could try installing **fs-driver.**

---

### Post by augusto.sisa on 2008-06-05
First, Thanks for your help.

I can boot ubuntu or XP without problems. 

When I installed Ubuntu, I physically unplug the internal HD to protect my WinXP partitions and after that I made the installation easily, and  save grub in /dev/sda. I set in the boot sequence USB  before internal disk so If the USB drive is connected to the laptop it loads ubuntu if not it loads XP.

As logos34 says the problem is that I can access the external HD from XP, even in the disk management. 

Some years ago I had a similar scheme with Mandrake distribution and two internal Hard drives, but in that time the linux partitions were detected by the disk management.  So I agree it's  odd.

---

### Post by logos34 on 2008-06-05
check in control panel>system>hardware>devices

if windows can see the external it should appear under Universal serial bus controllers (maybe as 'mass storage' device).

But I wonder why a popup doesn't appear on the desktop as soon as you plug it in?

---

### Post by augusto.sisa on 2008-06-06
Thanks.

I install fs-driver on Windows. And now, I can see the drive in the disk manager and all is fine. 

I agree with logos34 about that is odd that I couldn't see the device before, but now everything is fine.

Augusto

---


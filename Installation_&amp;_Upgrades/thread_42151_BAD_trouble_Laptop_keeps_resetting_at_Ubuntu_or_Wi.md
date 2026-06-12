---
title: "BAD trouble: Laptop keeps resetting at Ubuntu or Windows XP Install"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by lark5000 on 2005-06-16
I originally had Windows XP on this laptop.  Then I put on Ubuntu and gave up since the internal modem and the PCMCIA one I bought couldn't get working.

I decided to put Windows XP back on, as I have no choice because its someone elses laptop.  Now the laptop keeps resetting at various stages during the install.  I thought it was an overheating problem, but I let it cool off all night and it didn't make a difference.  One time it reset at about the 80% mark on Windows installation.  Other times is resets right in the beginning.

So I tried installing Ubuntu, and it gave me a red screen saying "check /var/messages/log" and couldn't continue.   Could it be that the hard drive is hosed?  Any input would be appreciated.

I'm about to try a DOS start up disk and format the drive.  I'm thinking it may be a problem going from Ubuntu's ext3 format to fat32 or NTFS.  Either that or GRUB screwed things up.  Or its an overheating problem.  Or all these resets while the hard drive was working did physical damage....   arg.....

---

### Post by jerrykenny on 2005-06-17
A thing that can get messed up is the mbr of the hard drive, . . . try using a floppy with fdisk to see if there are any unknown partitions still lying around there.

Also try a linux distro with cfdisk to see if it reports the same partition table,  Gentoo is very good . . . . use cfdisk to remove them, then reinstall windows.

---

### Post by lark5000 on 2005-06-18
Well, I got it to work, and this is how...

Basically, the next chance I got after a reset, I selected the 'install windows xp using the existing file system' instead of 'format disk using NTFS or Fat32 (quick or full), then install'.  This allowed me to install until completion.

Hope this helps somebody in the future!

By the way, I read that the command 'fdisk /mbr' from a floppy (emergency boot disk) can fix a master boot record if it is damaged.  I didn't try this but I think it would have worked as well.

---


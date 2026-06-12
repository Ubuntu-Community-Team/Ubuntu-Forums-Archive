---
title: "[SOLVED] Grub Error 21 &amp;amp; musical hard drives"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by xenocideJane on 2007-09-02
I'm trying to install Feisty Fawn on a Vaio laptop (PCG-N505VE), but it wouldn't boot from the PCMCIA CD drive, so I removed the drive, found out it was too small for my purposes (6G), upgraded my (Apple) laptop drive (to 120G), and took the Apple drive (60G) to use in the Vaio (everyone follow that? It was a little bit of a shell game). I put the 60G (Toshiba) drive in a PC tower (homemade), booted from CD and installed Feisty Fawn.

But it didn't work...and seems to have installed itself on the (40G) PC drive that had Windows XP loaded on it. The 60G doesn't do a damn thing when I try to boot from it (in the Vaio or the tower), all I get is a blinking white cursor on a black screen. Keyboard input doesn't affect it. What my issue is (ha! like I only have one), however, is that the tower no longer boots!

I've now removed the 60G laptop drive, so it should no longer be messing things up. When I try to turn on the computer, I get:
[INDENT]GRUB loading stage 1.5
GRUB loading, please wait.....
error 21[/INDENT]
I've read [some of the other discussions]("http://ubuntuforums.org/showthread.php?t=296184&highlight=GRUB+loading%2C+please+wait...+Error+21") of similar problems, but my variables are different and I can't input anything or even boot from a CD.

I'm using USB input devices, which seems to effect my choices, at least at the beginning, so I will be trying to initialize the 60G drive without installing before I install it when I get my hands on an older keyboard. I do, however, need to fix the tower, since it won't even boot from CD so that I can reinstall XP onto it.

Any help would be *greatly* appreciated! Thank you!

---

### Post by logos34 on 2007-09-02
ouch...if you can no longer boot from your cdrom drive in the tower, then that really complicates matters...wonder why...are you SURE it's set first in the Bios device boot order?

Sounds like grub overwrote the windows bootloader on the MBR of the 40GB XP drive (it does that by default), while ubuntu installed on the 60GB toshiba laptop drive.  Windows partition should still be there.  If you could only boot from the live cd you could check it with 

**sudo fdisk -l** (lowercase L)

When you try to boot from the 60GB toshiba drive you get nothing because the bootloader is on the other drive.  Likewise, when you try to boot from the windows drive with the laptop drive removed, you get as far as grub stage1 on the mbr, but it errors out because it can't find your boot files on the linux root partition.  

Since windows is likely still there, all you need to do is 'fixmbr' from the recovery console on the XP install cd to restore the windows bootloader, but to do that you have to find a way to boot from the cdrom. Good luck.  But if you can manage that, then you can also [boot from the ubuntu live cd and reinstall grub to 60GB laptop drive]("http://ubuntuforums.org/showthread.php?t=224351"), plug it back into the Vaio and hope that works.

---

### Post by xenocideJane on 2007-09-03
Okay, so it boots off the Ubuntu install disk but not the XP; I have successfully partitioned & installed Ubuntu on the tower, *thank you so much*!

Now it doesn't recognize the 60G drive at all! But I'll work on that one later.

---

### Post by xenocideJane on 2007-09-17
Totally reinstalled and it works. Thank you for your help!

---

### Post by DrDweeb on 2007-12-16
Dude,

I have one of these lying around with Win2000 running on it.
I have a USB CR-RW with it and I think the disk is 20GB

I am happy to format the disk and start from scratch if that is appropriate.

Do you have advice or hints?
How does it run?
Incompatibilities?

This is my first foray into the Linux world, so "be gentle"


Dr Dweeb.

---


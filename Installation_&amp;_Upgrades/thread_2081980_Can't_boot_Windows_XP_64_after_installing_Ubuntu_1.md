---
title: "Can't boot Windows XP 64 after installing Ubuntu 12"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by CalmDownMonkey on 2012-11-08
Hi,

I created a 100GB partition on my hard disk and installed Ubuntu (12.10 64-bit) onto it, leaving the Windows partition in place for a dual boot. I've done this uncountable times before, and it's never been an issue.

However, this time, when I select "Windows XP" from GRUB, I get a blinking cursor at the top left of a black screen, with 5 seconds of HDD activity, then absolutely nothing. It stays there indefinitely. 

I've played around with boot-repair and tried a few suggestions from other threads, but that either seems to end with the same result, or even prevent GRUB from appearing.

It gave me this URL to paste onto forums:
[http://paste.ubuntu.com/1341232/](http://paste.ubuntu.com/1341232/)

Is anyone able to understand anything from that? Or perhaps suggest "boot-repair" options that might work for me?

I'm hoping to fix it before Saturday for a LAN party, or I'm going to be a sad empty-handed nerd =( 

Thanks very much!

---

### Post by mastablasta on 2012-11-08
are you sure that everyhtign is OK with windows install? you could do fixmbr from windows repair console and see if you can boot into windows then. if all is ok then do the boot repair again to get GRUB back instead of widnows bootloader.

---

### Post by CalmDownMonkey on 2012-11-08
Thanks, I'll try using the Windows Recovery Console =D Hopefully I can find my CD drive, and the CD itself (I ditched the drive a while ago to save weight for carrying the PC to LAN parties).

Is there a way to do this from within Ubuntu? That still boots fine. Otherwise, I shall begin raiding my cupboards.

---

### Post by oldfred on 2012-11-08
Bootscript is not showing anything really wrong with Windows. Partition shows as NTFS, boot sector at least has some correct parameters that it checks and boot.ini looks ok. You have the three main boot files shown.

From Ubuntu you cannot run chkdsk which is often the main issue. I have run chkdsk from a Windows 7 repairUSB and it worked better than the XP chkdsk, but created a Windows 7 PBR - partition boot sector which I had to rewrite back to XP type PBR.

---


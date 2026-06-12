---
title: "Ubuntu (10.04 Lucid Lynx) Install Issues"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by kalinux98 on 2010-08-11
I've used Ubuntu in the past, and i have to say it's my favorite OS, so once i got a desktop i decided to install Ubuntu, at first i tried installing Karmic Koala, the install went 33% through and then it said there was a disk error, so i decided to download the new Ubuntu version (10.04). I downloaded the 32-bit version without any problems, burned the iso file on a DVD (i don't have a cd), and i reformatted my hard drive before installing. I put the Ubuntu disc in my drive and restarted my computer. The new Ubuntu load screen popped up, and i waited for the language selection screen to pop up like any other install. I waited for about a hour and then checked my computer it was still on the load screen. I then checked the console by pressing F1, and an area of code basically saying there was an error this was repeating over and over again. I made other copies of Ubuntu to see if the others would work, trying to make sure that the .iso file wasn't corrupted or didn't download properly. My computer-experienced father came in to help, and reformatted my hard drive with the Windows XP Install disc. After my looked at the BIOS and check if there was any issues, came up with some other options, we then tried a Lucid Lynx disc that i recently burned and this time it was different, after about 5 minutes I checked the console and it was making some progress. I immediately went back to the load screen and after a couple of seconds a screen of odd-colored blocks came up, my computer immediately froze after this. I restarted without checking the console at all and the same weird block-pattern came up as it froze. My dad then created a USB flash drive and made it into a Ubuntu 10.04 live USB. My dad then inserted the 4gig flash drive into my desktop and started it up, it did the exact same thing. :( Me and my dad don't have any experience with linux console commands so any help from experienced users will be acknowledged, thanks. :D

Here is my desktop's system specs:
RAM DDR2 2gigs
Intel Pentium 4 3ghz
XFX GeForce 8500 GT 512mb
ASRock 775Dual-VSTA Motherboard
(internal) HP DVD Writer dvd300i

Additional Info:
I burned my Ubuntu 10.04 Lucid Lynx .iso using the default Windows 7 Burner on my laptop and i burned it on an external iomega dvd drive.
I don't know if this will help but it's extra info. ;)

Update:
these messages pop up when trying to install(recent):
(process:314): GLib-WARNING **: getpwuid_r(): failed to unknown user id (0)
then on other lines it says there is an input/output error
there is also "SQUASHFS" errors and "I/O" errors.

---

### Post by kalinux98 on 2010-08-11
After waiting and watching the console it tells me there is "logical blocks", there was many SQUASHFS errors, and now I think it's saying  Buffer I/O error on device sr0, logical block ###### (numbers),  the number keeps going up and then it ends request, no idea what it is doing... Thanks in advance.

---

### Post by mörgæs on 2010-08-12
SquashFS is the file system used on the CD. It does not indicate a problem on the hard disk.

Have you tried another Linux for comparison, for example Knoppix?
[http://www.knopper.net/knoppix/](http://www.knopper.net/knoppix/)

---


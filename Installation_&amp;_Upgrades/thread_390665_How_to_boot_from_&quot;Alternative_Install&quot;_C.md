---
title: "How to boot from &quot;Alternative Install&quot; CD"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Hoosier205 on 2007-03-22
First of all....here is what I am working with on my laptop...

**Sony Vaio PCG-K35**

**_Processor_**
Mobile Intel® Pentium® 4 Processor
532 (3.06GHz1, 1MB L2 Cache)

**_Front Side Bus Speed_**
533MHz

**_Chipset_**
ATI Radeon™ IGP 345M

**_Integrated Wireless LAN_**
IEEE 802.11b/g3

**_LCD_**
15.4” WXGA with XBRITE™
Technology (1280x800)

**_Hard Drive_**
80GB2

**_Memory_**
1GB PC-2100 266MHz DDR
(512MB x 2)

**_Graphics_**
ATI Radeon™ IGP 345M
64MB Video RAM (shared w/ Main
Memory)

**_Operating System_**
Microsoft® Windows®
XP Home Edition

Now for my problem. I have tried to install a dual boot setup using the 6.10 Live CD (ubuntu-6.10-desktop-i386.iso). I was able to boot to the install and progress through it until reaching the partitioning portion. I did not proceed any further...backed out and rebooted into XP as normal to reread something on here about partitioning. Now, I can't even get back into the Ubuntu install. The first 2 times I got to the loading screen (with the status bar moving bank and forth), but it would just hang there. Now, I don't even get that far. I just have a black screen with a lone cursor blinking...taunting me. :)

So, I thought I would try the Alternative CD (ubuntu-6.10-alternate-i386.iso). Downloaded...burned....placed in tray for reboot. I reboot...goes straight to XP loading without even hesitating.

Both were verified twice, burned with imgburn at 1x.

By the way (as I may try to just get rid of XP and only install Ubuntu)...my lone reason for keeping XP...my iPod. Yes, I know there are Linux programs that can do what iTunes can do, but I also convert a lot of DVD's and AVI's to put on there. I was going to get comfortable wit doing this on Ubuntu first, before getting rid of XP. Just an FYI>..

---

### Post by louis_nichols on 2007-03-22
Did you check that the BIOS booting sequence is right? On some laptops there are utilities that set booting priorities straight from the the Windows Control Panel, without entering BIOS setup at boot.

Also, did you check the MD5 sums of the ISO images? Just to make sure the file was downloaded right.

---

### Post by buuntuu! on 2007-03-22
strange that it worked once but then taunted you... you didn't do anything wrong as far as i can see, i even played around with gparted and backed out from there when i installed...
just a stupid idea, did you reset the bootorder in bios when backing out of the first install??
sometimes it is the simple things we fail to see...

---

### Post by Hoosier205 on 2007-03-22
Yes, I checked the MD5 sum from Windows and then checked the CD when rebooting also.

I only have 4 "devices" listed in the boot order via my BIOS...

Optical
Hard Drive
Network
The other may be floppy (which I don't have anyway)...I'm not at the computer and can't remember.

Either way...I've made sure that my CD/DVD drive is the first to boot.

One little note...it's burned to a DVD+R...I didn't have any CD-R's available at the time. That couldn't be the problem could it?

Thanks for the help so far...I appreciate it.

---

### Post by louis_nichols on 2007-03-22
Hm... The CD/DVD thing shouldn't be an issue. But I guess that it might depend on the software you used to burn it. For example, when I use k3b to burn ISO images, it will ask me to select a different option if I have a CD or DVD in the tray, although it is the same image.

My suggestion is that you first check the DVD you burned in another computer and see whether it works or not. I mean, there are a dozen things that can be wrong with a burned CD's or DVD's. It seems to me higly unlikely that it is the computer's fault.

---

### Post by Hoosier205 on 2007-03-22
> **louis_nichols said:**
> Hm... The CD/DVD thing shouldn't be an issue. But I guess that it might depend on the software you used to burn it. For example, when I use k3b to burn ISO images, it will ask me to select a different option if I have a CD or DVD in the tray, although it is the same image.

My suggestion is that you first check the DVD you burned in another computer and see whether it works or not. I mean, there are a dozen things that can be wrong with a burned CD's or DVD's. It seems to me higly unlikely that it is the computer's fault.

I guess I'll just try it on a CD instead...I don't know what else to do.

---

### Post by Hoosier205 on 2007-03-23
I reburned to a CD-R this time....it worked! I know have a working dual-boot system. Now I just need to get used to using Ubuntu instead of XP.

---


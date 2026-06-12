---
title: "initramfs) unable to find a medium containing a live file system."
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by SHAMIM_HAIDER33 on 2011-09-26
Hi,

I am trying to install UBUNTU 10.04; 10.10 & 11.04 on my PC but every time it shows an error as follows :-


BuzyBox V1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) unable to find a medium containing a live file system.



My hardware configuration is:-
Processor:- Core i3
RAM:-2GB
Motherbord:- Gegabyte DDR
LG DVD R/W Drive

I have already Win-xp running on it on a different partetion.
Can anyone tell me the solution.

Thank you !

---

### Post by MountainX on 2011-12-09
make sure your USB disk is not plugged into a USB 3.0 port and make sure the md5sum on your iso image is correct.

---

### Post by Rubi1200 on 2011-12-10
Hi and welcome to the forums SHAMIM_HAIDER33 :)

Here is the link for the md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also make sure you burn the image at the lowest possible speed and that the optical drive is not damaged or dirty.

---

### Post by Lupi on 2012-01-22
I had the same problem, but after visiting this link [http://www.commodore-amiga.org/en/forum/8-commodore-os-howto-and-help/9984-unable-to-find-a-medium-containing-a-live-file-system](http://www.commodore-amiga.org/en/forum/8-commodore-os-howto-and-help/9984-unable-to-find-a-medium-containing-a-live-file-system) , I changed the SATA controller type from IDE to AHCI in Bios and everything works perfectly.

---

### Post by SiliconS on 2012-03-22
Thank you Lupi. That was a great tip.

---

### Post by przemnet on 2012-05-13
I had the same error and in my case solution was to disconnect Edimax USB wireless card. After live system started I connected the USB wifi card again (to have Internet connection during installation) and everything went fine.

**So a general piece of advice would be to disconnect all unnecessary USB devices when booting from USB stick and connect them after system starts.**

BTW it's a shame that developers did not test such a case where some other USB devices are connected during system boot. It's quite logical that it was not possible to find live file system on USB wireless card, but installer should be written in a way that it should somehow recognize type of USB devices and be able to find USB stick with required files. Especially in LTS edition...

---

### Post by Kenny-HUN on 2012-06-10
Two out of three configurations I have, Linux simply fails even to boot in the LiveCD... and people wonder why Linux is unable to spread...

I tried the 12.04 LTS AMD64 LiveCD burned on a DVD. (on other systems works fine, won't waste a CD) Previous versions do the very same thing, x86 as well.
/Edit: OpenSuSE 12.1 does the same, so it's a lovely kernel bug again for sure.../
The mainboard is an ASUS F1A75V-Pro, the rest shouldn't make a differnece. (shouldn't)

Only one thought, merely for the records, BIOS settings are set in a certain way for a reason (normally), by-passing and overriding them is NOT a smart idea. Windows is blamed of trying to outsmart the user, Linux tries to outsmart the hardware, again and again... epic fail.

---

### Post by repager on 2012-07-02
I have encountered this problem with Ubuntu and installed Centos 6 with no problem.
Having been using and installing GNU/Linux on many different desktops and laptops I find Kenny-Hun's comments rather amusing.
So Linux is not more successful on Desktop becuse it tries to 'outsmart' the hardware - nothing to do with Microsoft pressurising manufacturers to keep information secret resulting in the need to reverse engineer?
Even with this disadvantage Linux leaves Mcrosoft in the dust on many aspects of smooth hardware recognition on the fly.

---

### Post by lewis886 on 2012-07-26
i am trying to run ubuntu from a live cd.  the computer doesn't have a hard drive currrently. i am getting this same message.  i tried first with a disc for 11.04.  that gave me this message, so following some suggestions that i found, i downloaded 12.04 and burnt the disc at the lowest speed that my drive would go.  trying to boot up the computer with this new cd still gives me the same message.  

any ideas or suggestions?

---

### Post by Priyanka1811 on 2012-09-01
Hey I am facing the same problem and i am trying to install it from a iso file which is on my windows 7.
Please help me with a solution asap !!!

---

### Post by oldos2er on 2012-09-01
Priyanka1811, please start a new thread for your question. No one's likely to see it here tagged onto a year-old thread.

---

### Post by batpoep on 2012-11-06
Hi there, 

I was having the same issues, and then figured that it was a bios error (tried both a boot CD and USB), so tinkered there.  

I eventually found a setting to try boot into a Windows environment. 

[B]> Advanced Bios Features > Installer OS Select > Windows / *Other*
[/B]
After changing that, it all worked perfectly.

(Acer Extensa E264 with AMBios CMOS 2.5)

---

### Post by wildmanne39 on 2012-11-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---


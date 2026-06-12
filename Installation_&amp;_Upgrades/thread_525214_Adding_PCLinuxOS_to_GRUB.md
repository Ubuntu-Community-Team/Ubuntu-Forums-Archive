---
title: "Adding PCLinuxOS to GRUB"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by el mariachi on 2007-08-14
I really messed things up when I installed PCLinuxOS (I never tried another Linux distro besides Ubuntu so I decided to give it a shot).

PCLOS overwrited GRUB and I couldn't boot to Ubuntu. After running a few commands in the grub shell I could restore it and it booted Ubuntu again BUT PCLOS didn't appear as an option. So I downloaded Super Grub Disk and without me understanding it I messed the MBR's up.

This is how my HD's are configured:
SDA:
[LIST]
[*]SDA1 (stuff)
[*]SDA5 (PCLinuxOS)
[/LIST]

SDB:
[LIST]
[*]SDB1 (Windowsss Xp)
[*]SDB2 (/ of Ubuntu)
[*]SDB3 (/usr - Ubuntu)
[*]SDB4 (Swap)
[/LIST]

SDC:
[LIST]
[*]SDC1 (/home -Ubuntu)
[/LIST]

How do I make GRUB aware of all the OSes on my system?

---

### Post by kidders on 2007-08-15
Hi there,

The grub installer is available for a wide variety of operating systems. You can use any one of them (eg one of your Linuxes) to install a bootloader containing any menu entries you like.

When installed by Ubuntu, grub is configured to read its menu contents from /boot/grub/menu.lst, so if you like, you can add some extra lines for your other Linuxes to that file & use Ubuntu's grub installer to set up your MBR. Any subsequent changes you make to the menu file take effect immediately, so you can add & remove stuff at will, without having to do anything special.

Of course, a problem arises when something that *isn't* Ubuntu decides it wants to rewrite your bootloader. How best to handle that is entirely up to you.

---

### Post by louieb on 2007-08-15
Find the section of this site on chainloading or using a configfile. Thats the easiest way to boot more that one Linux distro.   [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by MQMike on 2007-08-15
Should be fairly easy to fix.

Looks like your BIOS boots from sda first?

If so, you need to do two things:

1   Reinstall GRUB from your Ubuntu to the Master Boot Record of the first (BIOS-bootable) hard drive.

2  Then, in Ubuntu, access your GRUB boot menu (/boot/grub/menu.lst) and make sure you have valid boot entries for the OSs you want to boot:  Windows, Ubuntu, and PCLinuxOS.  You can get the PCLinuxOS boot data from PCLInuxOS files – somewhere it must have a boot menu it keeps for itself.  Or use a configfile statement to boot it from the GRUB boot menu (kept at Ubuntu, /boot/grub/menu.lst).

Use these links to figure out the details:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Scroll down after post 1 for various topics)

Comment:  It looks like you put Windows on a non-first hard drive; i.e., the second hard drive.  If so, that may require using map commands to boot it.  In the 2nd link, scroll down the posts until you see that topic:  Windows on a non-first hard drive.

---


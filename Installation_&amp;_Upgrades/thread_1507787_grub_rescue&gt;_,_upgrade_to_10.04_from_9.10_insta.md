---
title: "grub rescue&gt; , upgrade to 10.04 from 9.10 installed via wubi in XP"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by freetop on 2010-06-12
Hi , guys
I install ubuntu 9.10 via wubi in XP.
I upgrade it to 10.04LTS
After reboot, I can't enter into neither ubuntu nor XP
the screen prompt:
> [SIZE=3][FONT="Arial Black"]erro:no such device:9c8f046f-d2c9-40c4-ab2b-a0c1266e62d2.
grub rescue>[/FONT][/SIZE]

There are three partition in my computer, i.e. , c:,d:,e:
I intall ubuntu in d:

I have replaced wubildr with patch from [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10"), but it doesn't work.:(

Help me!

---

### Post by oldfred on 2010-06-12
Did you install grub to the MBR and/or the windows partition? Wubi boots with the windows boot in the MBR first, then you choose Ubuntu and it shows the normal grub screen, but does not really use grub to boot.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by freetop on 2010-06-13
> **oldfred said:**
> Did you install grub to the MBR and/or the windows partition? Wubi boots with the windows boot in the MBR first, then you choose Ubuntu and it shows the normal grub screen, but does not really use grub to boot.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.
hi,oldfred
   thanks for your reply.
   yes, during upgrade to Grub 2, I selected dev0 which  GRUB was installed on. Is it the reason cause this problem, that Grub 2 override MBR which should be XP's?

---

### Post by darkod on 2010-06-13
> **freetop said:**
> hi,oldfred
   thanks for your reply.
   yes, during upgrade to Grub 2, I selected dev0 which  GRUB was installed on. Is it the reason cause this problem, that Grub 2 override MBR which should be XP's?

Yes, most probably. Run the script as suggested for more detailed info.

---

### Post by d3v1150m471c on 2010-06-13
wubi is almost always a bad idea. Use the live cd

---

### Post by freetop on 2010-06-18
> **darkod said:**
> Yes, most probably. Run the script as suggested for more detailed info.

Now I booted by live CD. and run this Script , got the result. How should I do next?
RESULT.Txt is in attatchments: [ATTACH]160793[/ATTACH]

---

### Post by oldfred on 2010-06-18
With Wubi you do not install grub to the MBR. Wubi boot thru the windows boot loader.

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)

Edit Boot.ini
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

You need to be sure to have an entry like this in boot.ini

c:\wubildr.mbr="Ubuntu-Linux"

---


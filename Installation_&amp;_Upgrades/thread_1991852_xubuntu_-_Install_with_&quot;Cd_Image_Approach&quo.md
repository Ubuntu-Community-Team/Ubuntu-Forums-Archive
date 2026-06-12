---
title: "xubuntu - Install with &quot;Cd Image Approach&quot; failed"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by sherjeel on 2012-05-31
[FONT=Arial][SIZE=3]I've a system with Windows XP already installed on 5GB NTFS partition. There are two other partitions as well but they are FAT32 and less than 8GB each.
The system has the following specifications:
Intel PIII 800Mhz
Intel Motherboard (with no support of boot from USB)
RAM 256
HDD 40GB
No CD/DVD Drive :sad:

I'm trying to install Xubuntu via "The CD image approach" as described on[/SIZE][/FONT] [FONT=Arial][SIZE=3]
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)[/SIZE][/FONT] [FONT=Arial][SIZE=3]

The link to download vmlinuz and initrd.gz are for gutsy but I downloaded the correct ones for Precise from:[/SIZE][/FONT] [FONT=Arial][SIZE=3]
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/hd-media/)[/SIZE][/FONT]  [FONT=Arial][SIZE=3]

Downloaded "xubuntu-12.04-alternate-i386.iso" and verified its md5 hash that is:[/SIZE][/FONT] [FONT=Arial][SIZE=3]
c80c298a 8b8d27f2 33294613 74eb5360

Now put everything appropriately.[/SIZE][/FONT] [FONT=Arial][SIZE=3]

Restart and installation begins.[/SIZE][/FONT] [FONT=Arial][SIZE=3]
But after Keyboard selection, when it comes to "Scan Hard drives for an installer ISO image", a message appears:
"Installation step failed....
The failing step is: Scan hard drives for an installer ISO image"

Later I also tried to put the hd-media and ISO image on FAT32 and made appropriate changes to "menu.lst". The installation started but again the SAME FAILURE on "Scan Hard drives for an installer ISO image"[/SIZE][/FONT] [FONT=Arial][SIZE=3]

What's going wrong? [/SIZE][/FONT] [FONT=Arial][SIZE=3]
Is there a reason that the mentioned procedure is applicable to Ubuntu only, and it is not for the Xubuntu?

Although I know there are other routes of installation, yet I found "CD Image Approach" much awesome [/SIZE][/FONT] [FONT=Arial][SIZE=3]:) So kindly help in this regard.[/SIZE][/FONT]

---


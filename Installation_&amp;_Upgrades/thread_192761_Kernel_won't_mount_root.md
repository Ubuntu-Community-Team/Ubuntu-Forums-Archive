---
title: "Kernel won't mount root"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by Whity on 2006-06-09
I have a very annoying problem, now I have of course searched the forum for anwsers and didn't find anything helpful, so I will explain what my problem is and hopefully someone can help. I'll start off with my specs (related to my problem):

3.0Ghz Intel P4
160GB SATA HDD (This is the HDD running Ubuntu)
Ubuntu is on sda1 using reiserFS
Dapper
Creative SB Live
Intel Onboard Sound
Nvidia Geforce 6600 GT

My problem is I can only boot Dapper from the 2.6.12-9 Kernel - which I am finding slow and laggish, this wasn't the case with Breezy. Also using this kernel Ubuntu can not pick up any sound drivers:
> whity@Daves:~$ sudo cat /proc/asound/cards
--- no soundcards --- This also was not the case with Breezy. Breezy of course used 2.6.12-9 kernel before I upgraded to Dapper.

Now the dapper installation installed the Kernel 2.6.15-23 which does not like to boot at all. Here is what is produced when I select 2.6.15-23 from grub.
> Uncompressing Linux... Ok Booting the kernel
mount: Mounting /root/sda1 /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No suck file or directory
mount: Mounting /sys /root/sys failed: No such file or directory
mount: Mounting /pro /root/pro failed: No such file or directory
Target filesystem doesn't have /sbin/init


Busybox v1.01 (debian 1:1.01-4ubuntu3) Built-in shell (ash)

Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
#


Now I thought this may just be a screwed kernel, so I decided to try 2.6.16-ck3 which produced the same result.

The other problem that I've had that may be related to the kernel issue, is Dapper hates the Nvidia drivers from AutomatiX and forces Xorg to throw a fit, forcing me to go back to the default config.

Also I don't know if this is worth mentioning, but the 2.6.15-23 kernel using the GUI boot thing until it gets to mounting root file system, where the 2.6.16-ck3 just has a blank screen for a few seconds, then goes to the console thing.

---

### Post by metoo on 2006-06-09
Do you have more HDDs installed. Many people have problems due to the fact, that drapper numbers the HDDs differently if the are attached to different S-ATA/IDE chips.
So if there are more HDDs may be on additional chip sets this could be a reason.

You can edit the device from within grub to test:
When you see the grub menu select the new kernel/drapper but don't hit enter but 'e' .
Exchange sda1 with different device ids like sdb1 or more likely sdc1/sdd1/sde1/
If the first chip set has 2 S-ATA ports sdc1 would be a good bet, if it has 4 sde1 could do the trick.

Lucky you if this works, but a change by this is not permanent. Once you booted into drapper, you have to edit the device id for this entry in the grub menu   /boot/grub/menu.lst   to make it permanent.

---

### Post by rbalfour on 2006-06-20
Yep it works! 

Here is my set up.

Dell SC420

On board SATA x 2

PCI Card SATA x 2

Onboard SATA Port 1 = sdc
Onboard SATA Port 2 = sdd

PCI Card Port 1 = sda
PCI Card Port 2 = sdb

Hope this will help other ppl too.

---

### Post by helpmeplease on 2006-08-28
Hi

I had a the same "kinda" thing happen with Dapper drake 606 on a Asus a7v mobo chipped up with a AMD 1200 cpu, everytime it would hang for 1 min 35 secs at the mount root point.

I cured it after reading the post above which pointed me in the right direction 

The post that mentioned running seperate HDDs! on different controller chips?

I looked in the A7v bios, and found that the SCSSI Symbiosis was enabled.

I dissabled it, and ..."hey preston" it now boots up in circa 30/40 seconds


I hope this can be of some help to anyone with a similar setup?


kindest regards to you all 


:D

---


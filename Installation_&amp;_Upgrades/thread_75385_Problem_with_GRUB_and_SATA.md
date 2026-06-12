---
title: "Problem with GRUB and SATA"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Guigui on 2005-10-13
Hi,

I recently tried to install Ubuntu on my PC. Everything goes fine until I restart after installing GRUB.

I tried Ubuntu 5.04 and Gentoo 2005.1 and got the same error message: when I select the system I want to boot with, it says "cannot mount filesystem" or "invalid filesystem"
Then I retried yesterday with Ubuntu 5.10. This time GRUB doesn't load, I only see GRUB_ at the bottom of the screen.

Here's my HD configuration

1st HD: WD Raptor 36Gb SATA, used for Windows XP
2nd: WD 80Gb SATA
           1st partition: 40Gb ext3 for linux
           2nd : 2Gb Swap partition 
           3rd: NTFS
3rd: WD 200Gb SATA: NTFS

I don't know why but they're detected in this order:

200Gb --> sda
36Gb   --> sdb
80Gb   --> sdc

Anyone had this problem and knows how to fix it?

---

### Post by Guigui on 2005-10-13
I dunno if this could help, I'm using the AMD64 version and here's my hardware.

Athlon 64 3500+
Asus A8N-SLI
2x512Mb DDR400 Corsair XL Pro
Asus 6600GT 128Mb

---

### Post by sander marechal on 2005-10-13
I have had problems too. Here's what I have:

80 GB SATA
80 GB IDE

The IDE came from my old computer and had my personal files on it (in partition 4) and partition 1-3 had an old warty install but mounted somewhere in /media. The SATA was set up for breezy by editing the partitions table.

Upon trying tio install grub I had to tell the installer where to install it. I told it to install in /dev/sda (boot partition of SATA). Upon restarting, GRUB would load but when trying to boot breezy it said "file not found" on the kernel image.

I reinstalled breezy, but this time I removed partition 1-3 from the IDE disk, leaving only partition 4 with my files on it intact. This time the installer did NOT ask where to install GRUB. Upon reboot -> error. GRUB loaded but when trying to boot breezy it said on the "root (hd1,0)" command: "partition not found".

Then I simply yanked the flatcable from my IDE and reinstalled breezy for the 3rd time. This time it worked. I'll see about adding that IDE drive later.

In short: Installation was definately not as it should be. Any place I can report these bugs? They should really be fixed ASAP.

---

### Post by Guigui on 2005-10-14
Anyone can help? :-k

---

### Post by sander marechal on 2005-10-14
Hmmm... I really thought I replied to this.... Oh well, I'll post again.

I made a comment about this in bugzilla ([http://bugzilla.ubuntu.com/show_bug.cgi?id=14959](http://bugzilla.ubuntu.com/show_bug.cgi?id=14959)) and I spotted a possible cure. Fire up your PC. When GRUB fails to boot linux, hit "e" to edit the boot script. The first line reads something like:

root(hd1,0)

This should be

root(hd0,0)

Then hit "b" to boot. Alternatively you can do what I did: Yank out the cables from your extra had drives leaving just one, install breezy, then add your drives back again. Ofcourse this only works if you plan to install breezy on that single disk instead of spreading the base directories over multiple disks.

--
Sander

---

### Post by Guigui on 2005-10-14
yeah I see root(hd1,0) but since my Raptor(sdb) is the boot disk hd1 should be ok. I tried changing it and it didn't work.

---

### Post by sander marechal on 2005-10-14
Hmmm... all I can recommend then is diving into the GRUB manuals and see if your boot parameters are wrong somehow. I am not really familliar with those so I'll let someone more knowledgable take it from here.

---

### Post by Guigui on 2005-10-15
Any other ideas?

Is SATA fully compatible with Linux or GRUB??

---

### Post by ProfHawking on 2005-10-16
Ive got a big problem with my system. When i try to install ubuntu, it goes through everything, up to the "installing Grub boot loader" point before the supposed reboot. at which point it hangs on 0% for ages. Does this normally take an hour?
Anyone got any ideas how to get round it? It wont boot from the HDD, and ive tried doing the install a couple of times to no avail.
Any help much appreciated

Base unit is a Shuttle XPC with AMD3200 athlonxp, installing on SATA seagate hdd. (others unplugged).

---

### Post by sander marechal on 2005-10-18
[QUOTE=Guigui]Any other ideas?

Is SATA fully compatible with Linux or GRUB??[/QUOTE]

I have no problem running it so far. I just unplugged all drives except one (a SATA drive), installed Breezy and then plugged the drives back in. Everything works smooth. The installer should be fixed though but this is a workable workaround.

One thing you might want to check: The boot order in your BIOS and the bootable flags on your partitions.

---

### Post by CrunchyDoodle on 2005-10-18
I am having a similar problem with GRUB failing to get my USB hard drive mounted when it executes its kernel command. It appears that the initrd image it's using at that time has only /dev/hda devices and no /dev/sda devices. It seems some of you need /dev/sda1 to be there as I do. I'm looking into adding SCSI drives to the image. Being a total Linux and ubuntu novice, it will be a struggle.    :) 

Bye.    :cool:

---

### Post by Iandefor on 2005-10-18
[QUOTE=ProfHawking]Ive got a big problem with my system. When i try to install ubuntu, it goes through everything, up to the "installing Grub boot loader" point before the supposed reboot. at which point it hangs on 0% for ages. Does this normally take an hour?
Anyone got any ideas how to get round it? It wont boot from the HDD, and ive tried doing the install a couple of times to no avail.
Any help much appreciated

Base unit is a Shuttle XPC with AMD3200 athlonxp, installing on SATA seagate hdd. (others unplugged).[/QUOTE]
installing LILO instead. I really can't help beyond that, because I never play around with bootloaders.

---

### Post by gomaaa on 2006-01-17
I have also had problems installing to a SATA hard drive and I believe there are several other people having similar difficulties.  I have tried to collect links to some of these issues and describe my own problem in the following thread:

[http://ubuntuforums.org/showthread.php?p=664688#post664688]("http://ubuntuforums.org/showthread.php?p=664688#post664688")


I hope that a general solution can be found!

gomaaa

---

### Post by guy_smiley:) on 2006-01-17
Methinks, but I'm not sure, as you guys haven't gone into much detail re:installation process, but have you tried the expert installation method? I believe this will allow you to load a SATA driver to allow for installation. I'm not sure if this will solve your problem, as I haven't done an install recently, lil later today prolly, but I hope it helps.

EDIT: No no no no no. It doesn't work! There isn't something that helps you with SATA in the installation process. I tried this, but it didn't work. I finally managed to get it installed, after many expert installs, and grub did load. The problem was that it loaded grub onto the IDE master (hda1) and therefore completely screwed up. I corrected this by changing the default drive by which my system loads, and it works! Grub works! The only problem I have now is to sort out the failed installation...

---

### Post by cweekly on 2006-02-14
hey guy_smiley
I too have a sata hdd (sda) on a brand new amd64x2 system, partitioned as 
/sda1 /boot (bootable)
/sda2 swap
/sda3 /

you wrote a couple weeks ago:
> I finally managed to get it installed, after many expert installs, and grub did load. The problem was that it loaded grub onto the IDE master (hda1) and therefore completely screwed up. I corrected this by changing the default drive by which my system loads, and it works! Grub works!

...but how precisely did you "...change the default drive by which [your] system loads" ?

I know I want the bootloader to be installed on /sda1 (not /hda1 or whatever it's currently assuming by default), but it's not at all clear how to change this during ubuntu breezy 5.10 install. 

thanks in advance for any reply

/chris

p.s. my first post, first experience w ubuntu and/or its forums...

---

### Post by malmjako on 2006-02-14
I have similar problems, because of the internal memory card reader getting different sd* sometimes (probably influenced by whether the external USB disk is running or not at boot). I'm thinking that /boot/grub/devices.map is a key in some way... Does anyone know what it does? Haven't had time to experiment with it, but I thought I'd share the thought.

---

### Post by cweekly on 2006-02-14
hi folks,

sorry, not sure I can help w your question malmjako.

I wanted to post an update my issue: 
went through "expert" install instead of standard, and during partition step chose to mount "/boot" (mountpoint) as "/media/sda1" (label) and it worked like a charm. (using the default install, w same simple partition scheme, it tried to put grub on /media/hda1 which is my ide cd/dvd player and didn't let me tell it to put it in /media/sda1 which is my (only) hdd's boot partition.
shrug.

fyi, spent almost 40 hours with gentoo trying to get a simple system working, to no avail (setting up as server was no problem, and its "portage" package mgmt system is pretty cool -- but getting desktop running was a 30+ hour battle I lost. hate to give up but I have too many other demands on my time) 

by way of comparison I spent less than 2 hours total with ubuntu 5.10 breezy (amd64 version) and it's working great so far. :D

---

### Post by executex on 2006-02-14
I have a problem launching windows XP with GRUB, it says unknown file type.

But i am able to launch linux, so i think you guys have some sort of different problem.
launch GRUB, then press e on the line that doesnt work. then where it says root (hd0,0)

type this:
root (
then press TAB. IT should give you some choices if not type hd0. Then type a comma, then press tab again. And it will give you possible partitions.

Now if you know which one it is, edit it, press b, and try it.
if not post what the response was.

---

### Post by binger on 2007-10-21
I have been having similar problems with Grub/Linux.  I have a SATA hard drive and a PATA DVD drive.  I believe that the SATA drive loads first and takes memory blocks that makes the PATA driver fail afterwards.  I am about to try options suggested on the site below and will post an update of how things go.
[http://www.togaware.com/linux/survivor/SATA_CD_DVD.html](http://www.togaware.com/linux/survivor/SATA_CD_DVD.html)

---


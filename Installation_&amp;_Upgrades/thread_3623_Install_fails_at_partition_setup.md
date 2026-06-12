---
title: "Install fails at partition setup"
date: 2004-11-07
forum: Installation &amp; Upgrades
---

### Post by VoiDeR on 2004-11-07
Ive been hearing alot about Ubuntu so i figured id give it a try. After i setup the partitions and go to formate it i get this error

                                       Failed to create a file system
The ReiserFS file system creation in partition #4 of IDE1 Master (hda) failed.

I have tried diffrent file systems, different computers, and even redownloaded and reburn to different cd brands and still get the same messege. Any idea's i have Gentoo install  on hda2 a swap on hda1 and windows on hda3. I tried prepartitioning from gentoo but i still get the same error messege. Please help id really like to give this a try.

VoiDeR

---

### Post by SkyHook on 2004-11-08
I have noticed a similar situation recently. I originally installed Ubuntu and took the default partitioning scheme, all went well and I liked the distro so after a couple of days feeling my way around things(no experience with Gnome), I felt even more comfortable. I wanted to wipe everything clean and do a fresh install this time using ReiserFS. I am using a Western Digital 13 gig HD and was going to make a 6 gig "/" partition, a 6 gig "/home" partition, and 1 gig "swap" partition. Setting up the partitions went without a hitch but when I accepted everything and it tried to format "/" it said the exact same message as listed in the above post. As an experiment I backstep to the start of the procedure and selected the default scheme and when it presented the final screen before committing the changes and formating I selected the "/" partition and set it to ReiserFS and proceeded and it formated fine. After the install completed I turned right around and tried doing it again, once again specifying a 6 gig "/" a 6 gig "/home" and 1 gig "swap" and once again the format of "/" failed. Turned around and went the default route specifying ReiserFS for the "/" and that is the installation I'm running on right now so ReiserFS is possible but for some reason if you manually setup the partitions it has a problem.

Hope this experience helps isolate what might be going on here.

SkyHook

---

### Post by VoiDeR on 2004-11-08
[QUOTE=SkyHook]I have noticed a similar situation recently. I originally installed Ubuntu and took the default partitioning scheme, all went well and I liked the distro so after a couple of days feeling my way around things(no experience with Gnome), I felt even more comfortable. I wanted to wipe everything clean and do a fresh install this time using ReiserFS. I am using a Western Digital 13 gig HD and was going to make a 6 gig "/" partition, a 6 gig "/home" partition, and 1 gig "swap" partition. Setting up the partitions went without a hitch but when I accepted everything and it tried to format "/" it said the exact same message as listed in the above post. As an experiment I backstep to the start of the procedure and selected the default scheme and when it presented the final screen before committing the changes and formating I selected the "/" partition and set it to ReiserFS and proceeded and it formated fine. After the install completed I turned right around and tried doing it again, once again specifying a 6 gig "/" a 6 gig "/home" and 1 gig "swap" and once again the format of "/" failed. Turned around and went the default route specifying ReiserFS for the "/" and that is the installation I'm running on right now so ReiserFS is possible but for some reason if you manually setup the partitions it has a problem.

Hope this experience helps isolate what might be going on here.

SkyHook[/QUOTE]
 If i understand right you wiped your drive clean first. I cant do that. I don't understand what the problem is. It would be nice if i could get alittle more info about what failed. I guess ubuntu is out for me.

---

### Post by wallijonn on 2004-11-08
[QUOTE=VoiDeR]I guess ubuntu is out for me.[/QUOTE]

You give up too easily, friend.

If you know how to get to the Reiserfs menu, then go a little further into the manual script and then delete all the Linux partitions, create a / and 'accept' it. It should format and install the OS.

I find that I have no need to create separate paritions for /, /boot, /var, etc.

> Gentoo install on hda2 a swap on hda1 and windows on hda3.
Now you're playing with fire as Ubuntu is very likely to overwrite the MBR. Heck, I want to know how you got Windows on HDA3. :D

I was playing with VidaLinux and had to disable Gentoo from installing into the MBR. I then modified Ubuntu's GBRUB to point to Gentoo's vmlinuz.

---

### Post by VoiDeR on 2004-11-08
[QUOTE=wallijonn]You give up too easily, friend.

If you know how to get to the Reiserfs menu, then go a little further into the manual script and then delete all the Linux partitions, create a / and 'accept' it. It should format and install the OS.

I find that I have no need to create separate paritions for /, /boot, /var, etc.


Now you're playing with fire as Ubuntu is very likely to overwrite the MBR. Heck, I want to know how you got Windows on HDA3. :D

I was playing with VidaLinux and had to disable Gentoo from installing into the MBR. I then modified Ubuntu's GBRUB to point to Gentoo's vmlinuz.[/QUOTE]
 Believe me ive done that  hda4 is free space and i set it up as reiserfs and mount poing / then click done then click finish and then if fails. Ive tried every diffrent possibilaty except letting it erease my hole disk.  

As for rewriting my mbr. All i have to do is chroot into my gentoo  install and rerun and edit grub. No big deal i do it all the time. Ive never had windows complain about not being on hda1. 

VoiDeR

---

### Post by wallijonn on 2004-11-08
I find that if I install Linux first that I cannot install Windows98SE afterwards. But if I install Windows98SE first I can install Linux afterwards. Do you use Partition Magic?

---

### Post by VoiDeR on 2004-11-08
[QUOTE=wallijonn]I find that if I install Linux first that I cannot install Windows98SE afterwards. But if I install Windows98SE first I can install Linux afterwards. Do you use Partition Magic?[/QUOTE]
 I hate Partition Magic. If your only using it to move and resize windows partitions then its fine but, if theres a linux partition in it forget it. Anyway originaly it was setup 10gigs for gentoo and 10gigs for storage. Then i started haveing some hardware problems so i broke the 10gig storage in to 2 5gigs Installed windows 2000 on hda3 to make sure it wasnt a gentoo thing. I was going to install Ubuntu on hda4. I had debian installed on hda4 before and ran a sector scan. I at a lose at whats wrong.

VoiDeR

---

### Post by wallijonn on 2004-11-08
Do you have Norton Anti-Virus installed in WXP? Some programs protect the MBR from being written. Wouldn't the fourth partition be had3?

---

### Post by VoiDeR on 2004-11-08
[QUOTE=wallijonn]Do you have Norton Anti-Virus installed in WXP? Some programs protect the MBR from being written. Wouldn't the fourth partition be had3?[/QUOTE]
 No i dont have Nortan, Partition Magic trys to change some values or something and it screws up the partitions. Hda1 is my swap, hda2 is gentoo, hda3 is windows 2000, and hda4 would (hopefully) be Ubuntu.

---

### Post by hayalci on 2004-11-23
I have the same problem, and I dig a little.

dev nodes for partition are not created normally during install.
there is a /dev/ide/host..bus..target/lun0/part1
but my disk has hda1 hda5 hda6 hda7.
Gentoo livecd shows these properly.
but ubuntu shows only part1, when I list its interior
using fdisk,
partitions are shown as part1p1....part1p7

I don't know it is a "feature" of udev, but it causes partitons
fail at formatting. I tried to repartition and reformat with gentoo livecd,
but ubuntu cannot mount the / as well.

my disk is Maxtor 6L040J2 40G
I did not change partition sizes remaining from my former linux (mandrake)
and I certainly do not want to lose windows part and data part.

this seems like a bug. Any ideas. should we report it?

---

### Post by VoiDeR on 2004-11-27
Well i dont know what to do. If been using the livecd and really like it. I hope someone can figure out whats going on here.

VoiDeR

---


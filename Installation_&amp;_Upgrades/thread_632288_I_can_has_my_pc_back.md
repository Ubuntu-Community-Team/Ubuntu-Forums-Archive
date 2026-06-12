---
title: "I can has my pc back?"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by oromisthewise on 2007-12-05
I'm sure that there are similar threads to this by frankly i don't have the time or skill to find one that suits my needs.

 Basically i had everything i wanted in my pc (almost) until last night with Ubuntu gutsy and songbird and all my songs and videos etc, but i wanted to make a dual boot in order to play video games and such so i used the feisty livecd (the closest thing i had to hand) to create a 40gb partition on my 160gb western digital hard drive.

 if it makes any difference this took 2-3 hours, which i didn't expect, and it was an ntfs partition.

 Anyway the point is i installed xp on this partition (and i assure you i am totally certain that it was the right partition) and booted into it. most things worked fine and after a while i got annoyed with the driver hunting and tried to restart to Ubuntu to watch a movie but it wouldn't give me a choice of operating systems on boot and just skipped straight on to windows xp. 

 I went back into the feisty CD and looked at the partitions and saw that windows xp had the box checked that said "boot" in gparted, so assuming that this meant that that was the only drive that would be booted to and if i changed it back to my ext3 partition then grub would take over i did exactly that. but now it said that it could not find an OS and refuses to load.

 So long story short i got tired of xp and deleted the partition with xp on and merged it back with the rest of the drive and restarted, but i am still met with the same screen that says
"Error loading operating system" and does nothing about it.

 So now my carefully constructed collection of photos, apps and other media that i have accumulated since feisty is unaccessible and i don't have the means to do anything about it, as i don't have an external drive.

 The feisty livecd shows me that my media is all still there, it just doesn't want to boot to Ubuntu for some lame reason. I suspect that this is connected to windows xp wiping grub, but im a bit of a noob at these matters, which is why im writing this :(

 I'd really appreciate your suggestions and if anyone can point me to a guide to installing xp without messing up my beloved Ubuntu install, that would be awesome too.

[CENTER]HOPE I DIDNT BORE YOU TO DEATH TOO MUCH :)[/CENTER]

[edit]
also i know everythings still there cos i browsed my old files with the feisty livecd

---

### Post by PmDematagoda on 2007-12-05
It seems that your boot-loader was simply over-written by greedy XP, you can reinstall GRUB to the MBR using [Super GRUB.]("http://supergrub.forjamari.linex.org/?section=download") That will allow you to access Ubuntu again, provided it is still there.

---

### Post by oromisthewise on 2007-12-05
Thanks a lot! ive managed to boot into ubuntu with the cd though i havent fixed grub properly yet
:guitar:

---

### Post by Irony on 2007-12-05
Here's an example of how to install grub...

From a live CD do;

To install grub to the MBR (hda) and point it to a menu.lst in hda3 do;

[PHP]sudo grub[/PHP]

This opens up the grub program, with a prompt of grub>, now type. 

[PHP]find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit[/PHP]

Here is an example;

[PHP]grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit[/PHP]

---

### Post by gewitty on 2007-12-06
I have a similar problem. I was trying to install WIN XP to a slave drive on my machine. When I ran the install disk, it wanted a small partition created on the primary drive where Ubuntu is installed. I used Gparted to create a 3Gb partition and then continued with the installation. However, the next screen said that Windows had identified another OS and would have to make the partition it resided on inactive while installing XP. At this point I decided that I needed to do some more research before proceeding and abandoned the installation without allowing XP to interfere with Ubuntu - or so I thought. When I tried to restart the machine, I got an error message saying that no operating system could be found. I checked using a live CD and as far as I can see, all of the original installation is still intact, so I assume that the problem is with GRUB. I tried the fix mentioned above. The 'find' command returns (hd0,0),  but when I reach the point where I enter the 'setup (hd0)' command, I get an,  'Error 17, Cannot mount the selected partition', message. I checked which partitions are present on the drive and can see hda1, hda3 and hda5. Can anyone tell me where I'm going wrong?

---

### Post by gewitty on 2007-12-06
Super Grub did the trick. Thanks.

---


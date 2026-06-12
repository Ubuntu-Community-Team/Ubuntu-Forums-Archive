---
title: "How to reinstall Ubuntu 10.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by wandiligong on 2011-10-15
[FONT=Arial][SIZE=3]I am a complete Linux novice[/SIZE][/FONT]
[FONT=Arial][SIZE=3]PC 2.6 GHz processor 2 GB RAM two physical HDD 80 GB each running Win 7 successfully[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Trying to install Ububtu 10.10[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Ran live disc and seemed to operate OK[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Chose option to install &#8220;Alongside existing&#8221;[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Took a long time to install but seemed initially to be OK. But was unstable in for instance running RythmBox when an audio disc was inserted &#8211; sometimes launch sometimes not.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Then discovered that the dual boot initial screen did not work &#8211; unable to move highlighting to boot with Win 7 (or anything elese) keyboard would not move highlighted line. After 10 secs countdown booted to Ubuntu. However after a couple of such boots system now hangs on GRUB screen &#8211; count down now disappeared.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]I can still open Ubuntu with live DVD and think that perhaps if I reinstalled it might fix problem. But just how to reinstall is confusing me.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Using GParted I get the following:-[/SIZE][/FONT]
_[SIZE=3][FONT=Arial]/dev/sda1 71.45 GB[/FONT][/SIZE]_
[FONT=Arial][SIZE=3]/dev/sda1 ext 4 71.45 GB 3.4GB used 68.04GB unused Flag &#8211; boot[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev sda2 extended 3 GB[/SIZE][/FONT]
[FONT=Arial][SIZE=3]/dev/sda5 linux-swap 3 GB[/SIZE][/FONT]
_[SIZE=3][FONT=Arial]/dev sdb1 74.52GB[/FONT][/SIZE]_
[FONT=Arial][SIZE=3]/dev/sdb1 ntfs 74.5GB 13 GB used 61GB unused Flag &#8211; BOOT[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Unallocated 10.3GB[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]If I use live DVD and select install I eventually get to Allocate drive space screen[/SIZE][/FONT]
[FONT=Arial][SIZE=3]If I select &#8220;Alongside&#8221; option it shows for sda a graphic with Ubuntu 11.10 /dev/sda1 (ext 4) 38.8GB and Ubuntu /dev/sda2 (ext4) 37.9GB[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Selecting sdb (from this allocate drive space screen) I get a graphic showing Win NT/2000/XP (loader) /dev/sdb1 (ntfs) 45.7GB and Ubuntu /dev/sdb2 (ext 4) 34.3GB[/SIZE][/FONT]
[FONT=Arial][SIZE=3]In either of these screens if I select Install Now I get a Write previous changes to disc and continue? Message which says &#8220;Before I can select a new partition size &#8230;.etc&#8221;[/SIZE][/FONT]
[FONT=Arial][SIZE=3]I have read on the forum the suggestion that for a reinstall to select &#8220;Specify partitions manually&#8221; but this gives me a lot of info about disc space which I don&#8217;t understand and also asks where I want Bootloader put. Again I don&#8217;t understand.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Can anyone help with instructions on what to select to do a reinstall please.[/SIZE][/FONT]
[FONT=Arial][SIZE=3][/SIZE][/FONT] 
[FONT=Arial][SIZE=3]EDIT: Now found article on net how to reinstall - delete Linux partition. Did this and reinstalled. Seems OK but still cannot boot to Win 7 - GRUB screen will not allow highlighting of anything but Ubuntu?[/SIZE][/FONT]

---

### Post by varunendra on 2011-10-17
Is it a USB keyboard? If yes, try changing the USB support mode in BIOS, or follow suggestions on this bug-report page: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/60177](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/60177)

If this does not help, I would suggest to start a new thread with a relevant title (like "keyboard does not work at grub menu" or something similar and more relevant). You should then post a link to that thread here for others to follow.

---

### Post by wandiligong on 2011-10-17
Thank you Varun
 
I tried a non-USB keyboard and can now highlight in the GRUB screen. I will look further into your advised BUG
 
Needless to say although I can now select Windows there is an error and it will not load. It might be due to prior to installing Ubuntu I had Win 7 installed but Win 98SE files (uninstalled) on the system. I have a feeling that both Win 7 and Win 98 might have somehow come together.  I will try a Windows recovery disc later
 
Thanks for your help re ammending my posts. Forums can be confusing as a newbie - all I wanted to do was ask a question but Threads and Posts can confuse novices
 
Thanks again
 
Wandiligong

---

### Post by varunendra on 2011-10-18
You're welcome :)

As for the Win7 issue, my guess is that the win98 partition could have win7's boot files in it which were removed along with win98. Hence the win boot error. However, if you have a recovery disc, it should easily fix it, although it depends on what kind of recovery disc you have.

If you feel the need for support on that issue, you may post a new thread, and along with the problem's description, you should also post the output- "Result.txt" of **boot info script** which you can download from here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Directions to use it are given on the same page I linked above.

And don't worry about posting confusion. It'll all be familiar in no time, as users and mods are very friendly around here.

---


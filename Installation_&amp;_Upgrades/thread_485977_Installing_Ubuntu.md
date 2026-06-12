---
title: "Installing Ubuntu"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by YukonMaster on 2007-06-27
Ok I am using the live ubuntu now, and I want to install it on an empty partition as I have Vista Ultimate installed also. Now how do I do this, I am sorry but I am a noob when it comes to linux so alot of it is just jibble to me.


Thanks,

YukonMaster

---

### Post by dabl on 2007-06-27
Do you already have an empty partition?  If so, just click "Install" on the Live CD desktop, and point it to the empty partition.

If you don't have the empty partition, then everything I read indicates that you need to use Vista's re-partitioning function to do that, rather than Ubuntu/GParted's. I haven't done that myself. :)

---

### Post by 505 on 2007-06-27
If you have an empty partition, this is quite easy. Just double click the installation icon on the desktop once you booted the live session. Follow the directions in the screen. Only watch out where to install, select to install it to the empty partition, otherwise you could also delete the Vista partition. The rest should be automated. It will even install dual boot with Vista and Ubuntu.

---

### Post by ABCC on 2007-06-27
your best bet is to start flipping through the ubuntu guide, an exhaustive resource if ever there was one but it should be able to give you the jist of what is needed. you can find it [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"). on your desktop there should be an 'install to harddrive' icon, clicking that will take you to the installer. you need to ensure that you do _NOT_ use the default 'use the entire harddrive' option but instead decide on 'manually partition the drive' or 'use largest available free space' (or words to that effect).

if you dont have an empty partition i suggest you take a look at this [guidel]("http://www3.telus.net/linux4u/ubuntu.html") before you proceed. defragmenting your ntfs/vista drive is recommended, more so if it is quite full (75%+)

---

### Post by ABCC on 2007-06-27
lol how's that for a quick reply :D

---

### Post by anotherbigal on 2007-06-27
Hi all

Don't know about where to install, I am asking How to install.

I downloaded the 7.04 live CD, (MD5 is ok) and had a good look through all the info from within Windows. It all looks interesting so I decided to install my first ever version of Linux.

I have a new machine with 250 GB GB HDD. Partitioned 35 GB NTFS (Windows XP SP2 & Office 2003) Unallocated and unformated primary 35 GB (reserved for Ubuntu) then the remainder as extended with 3 FAT 32 logical partitions for data, backups and copies of software. - FAT 32s for easy access to contents from whichever Op Sys I am using. The machine has an Intel duel core processor and Intel motherboard and with 2 GB of memory. The HDD is on a SATA drive.

The instructions on the live CD say to boot into the CD to install. I can't. Some kind of memory error flashes up on the screen, to quick to read then after the Ubunto timer graphic the screen goes black ant the following appears:

[HTML]BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [ 33.606298] ata1.00: failed to set xfermode (err_mask=0x40)

[  68.766402] ata1.00:failed to set xfermode (err_mask=0x40)
[ 103.766402] ata1.00:failed to set xfermode (err_mask=0x4)
[ 135.766402] ata3.00:failed to set xfermode (err_mask=0x4)
[ 170.766402] ata3.00:failed to set xfermode (err_mask=0x4)
[ 206.766402] ata3.00:failed to set xfermode (err_mask=0x4)[/HTML]

I have run memory check for over 50 cycles and non errors were reported, so I asked for and received three CDs from Cononical (excellent I thought, I have customers that are interested), but they all fail in exactly the same way, but all reveal their contents without problem from within Windows.

I just do not understand what is going on, any suggestions anyone? By the way, the default boot order is floppy, CD, HDD, LAN.

---

### Post by merlinus on 2007-06-27
This sounds like a video problem.  Did you try Safe Video Mode?

You can also try the Alternate Desktop install cd, which is text-based.

-merlin

---

### Post by anotherbigal on 2007-06-27
Thank you for your input.

I have tried the Safe Video install but got the same problem. I'll try the desktop install. Hadn't thought of that.

---

### Post by anotherbigal on 2007-06-28
Has anyone got a link to the MD5 checsum page please. I have been looking everywhere for it?

---

### Post by ABCC on 2007-06-28
> **anotherbigal said:**
> Has anyone got a link to the MD5 checsum page please. I have been looking everywhere for it?

If I'm not mistaken the CD itself contains the MD5 checksum and the ability to do an 'integrity check'. If that's not the case you should be able to find the md5 sum through the download page. You'll be given the choice of umpteen mirrors to download from, each server should contain both the .iso and the .md5


This doesn't look like it has anything to do with your graphics at all.   'ata' tends to refer to block devices (harddrives, floppies and of course cd/dvd drives), which would suggest xfermode stands for transfermode. 

Ok, ive been googling around a bit and turned up a few hints, here's my search string so you can dig around a bit yourself too:  ata*.00:failed to set xfermode

Here's someone who claims to have had a similar type of problem with feisty, however his/her fix was to append an 'irqpoll' boot option to their grub.conf. Given that you're using the livecd that's not an option, but passing boot parameters is possible, I believe 'f3' will give you the options that you can pass. 

[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/]("http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/")

Without being able to check for myself to confirm that this option is possible from the liveCD I can't say for sure you will be able to try that particular one. I do know that many people simply have trouble with acpi/apm in particular (or perhaps dma), a bit of trial and error here could be all that you need. If this still fails, then please post a bit more info about your setup and we can look further.

HTH

ABCC

---

### Post by stchman on 2007-06-28
> **YukonMaster said:**
> Ok I am using the live ubuntu now, and I want to install it on an empty partition as I have Vista Ultimate installed also. Now how do I do this, I am sorry but I am a noob when it comes to linux so alot of it is just jibble to me.


Thanks,

YukonMaster

You need to be sure that the empty partition is free space.  If your partition is empty but formatted theen Ubuntu will not see it as free space.  Once you have some free space then you can just tell the Ubuntu installer to use the largest continuous free space.

---

### Post by anotherbigal on 2007-06-29
Thank you for the input ABCC.

I had downloaded the iso for an alternative install and wanted to check its integrity before burning it to a CD hence the request for the checksum page link.

From the standard LiveCD I tried altering the video setting via the function buttons at the bottom of the screen and this, at least in part, has solved the problem and enabled me to install Ubuntu where I wanted it. Booting up now gives me access to GRUB and the option to boot into Ubuntu or Windows.

However, when booting into Ubuntu I still get a flash of an error message. Too quick to read properly, but saying something about ....failed to allocate mem resources.... Is there any way I can find what that actually says so that I can either happily ignore it as the machine seems to be running ok, or, preferably, locate and fix the problem?

---

### Post by anotherbigal on 2007-06-29
Hi stchman

The free space was just that. Not formatted free space although computer management in Windows showed it as in sequence as the second primary partition.

I have at least in part solved the problem. Please see my reply below for details.

Thank you for your help

(Like your site by the way)

---


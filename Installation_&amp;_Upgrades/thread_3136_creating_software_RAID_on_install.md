---
title: "creating software RAID on install"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by somewhat on 2004-11-03
Hi there, I am currently in the proccess in choosing a distro for my upcoming fileserver and the main criteria is that I can install on a software RAID 1 partition.  I have always been a fan of Debian and have enjoyed what I have seen of Warty during some playing around in VMWare.  Anyhow after looking around I have so far found the following options...

**Gentoo:** Detailed howto's in their forums on how to achieve this when installing, however Ive used Gentoo quite a bit in the past and installed it far too many times (ie rule out a few days for this!)  and am not really wanting to use it for my fileserver, but is looking a good option for this criteria..

**Fedora:** Ive used Red Hat over the years and I know things have changed with rpms etc, but I still shudder when I think back to those days.  However a quick search of their forums shows that using Disk Druid during the installer, one can (apparantley) easily set up a software RAID to install on. 

**Ubuntu **(hoping!)  I have found some howtos for Debian so far, but they look pretty ugly ie install as usual, then create the RAID, merge data across or something...  Has anyone set up Ubuntu successfully this way?  Is anything planned for RAID during install for Hoary etc?

---

### Post by jdong on 2004-11-03
The ubuntu partitioner allows for creation of Software RAID.

Plus, setting up them manually on Gentoo or any Linux is roughly the same process, so all the Gentoo howto's apply. And copying over a filesystem is a much simpler process than installing a Gentoo system from scratch!

---

### Post by somewhat on 2004-11-04
Nice, thanks - had only installed Ubuntu once and didnt really explore the partitioner (wasnt interested in raid then)  Indeed you are correct about it letting me set up software raid, but I did get the following warning:

Ubuntu does not currently support using software RAID for the root filesystem or /boot partition.  A system installed in this way will not boot.

I take it this is the pretty standard Debian thing - so I will still have to do the ol install on one disk, then create array and copy procedure?

---

### Post by ChrisQ on 2004-11-14
I'd love to hear more about this. Did you get it to work with the installing on the / partition in software raid 1? Could you point me to the howto for gentoo to get this work?

---

### Post by TravisNewman on 2004-11-14
Kinda embarassing, but I didn't even know RAID was possible without a RAID controller! I guess I never did any research on it because I wasn't interested in it, but I'd definitely be interested in it now, so if it's possible to do raid on /, I'd love to know how (unless it would cause major problems. It's not worth it in that case).

---

### Post by mcwimpy on 2005-07-15
Hey Guys, i want to tell you my experience:

To take the tension away: SW RAID is possible with the Ubuntu installer CD. (I tested only 2005.4) The handling is rather complicated. Too much submenus. Uncomfortable, but working.

[SIZE=2]**my story:**[/SIZE]
I looked for a solution for my Silicon Image "Medley" fake RAID. Because this fuckers don't support the community with drivers or even information i guess, it's kinda hard to get it running and boot from it on Linux in general. I only made it with Gentoo. They have a nice solution provided by Gerte Hoogewerf:
[COLOR=Blue]http://tienstra4.flatnet.tudelft.nl/~gerte/gen2dmraid/[/COLOR]
see also
[COLOR=Blue]http://forums.gentoo.org/viewtopic-t-258981.html
[/COLOR]
From the Fedora and SUSE installation media you can't expect to be aided on this topic. I don't know about Ubuntu in this special case, as i decided to switch to SW RAID instead of this BIOS-fake-RAID 'cause of the mentioned issues and that's what was the outcome:

**1.) **You have to delete any M$ shit from you system or install it only on a hard drive apart from you SW RAID. Windows MUST NOT use the hard drives containing your software RAID!!! Caution!! It will delete your RAID partition informations and destroy your data if you let it touch you RAID drives. I lost a Installation of SUSE Linux 'cause of that. #-o [COLOR=Red]--> (*)[/COLOR]

**2.)** You have to completely define all partitions and md RAID definitions at the time you install you first Linux (if you are planning to install not only Ubuntu ...) eg I messed up my RAID sets, playing around on with the Ubuntu installer on a half finish set up md RAID configuration and lost a again my installation of SUSE Linux.  ](*,) So first install Ubuntu and define you RAID completely at installation time. After that you can install other Linuxes, which only USE your predefined partition definitions.

**3.a)** You need a normal PATA hard drive wit a small 32-80MB /boot partition. I suggest hda1 for it. there you store GRUB and the kernels of all distributions. (Beware!!! After a Ubuntu --> SUSE --> Fedora Installation i had to repair the SUSE installation with Yast2 'cause Fedora -- it was FC4t2 -- seemed to screw up some stuff on the /boot partition... (don't forget to save the distributions own /boot/grub/menu.lst to easyly copy paste the entrys there to the final one including all distributions)

**3.b)** Alternatively a /boot partition with RAID1 instead of RAID0 should allow you to dispense with the additional PATA drive. I didn't test it. I just read about it, so don't citate me. I use 1 PATA drive as primary master on IDE0 and 2 SATA drives containing some "Linux RAID" partitions formated with different filesystems. However: I use the PATA drive also to store my data (100GB mp3) 'cause i fear for them on a RAID0 and i don't want to waste half the space for RAID1 ...





[COLOR=Red](*)[/COLOR] be VERY carefull with M$ OSses in general, when useing at the same time a Linux. eg the WinXP_SP2 installer fucked up reproduceably my partition table when being confronted with a free space before the 1st (primary) partition (on the forst drive). :(  I could correct it with standard open-source tools, but if you are beginner maybe you can't.

Or you beliefe the M$ Installer when he smears down (and reboots) 'cause of this free space infront of his system partition and then (after messing up your partition table and booting a second time) tells you the hard drive has no partition table. If you then create new partitions you are lost.  [-X 

Leave the installer instead and reboot to a Linux rescue system. You just have to change back the partition ID with fdisk. And change the partition table to go without free space in front of the first partition. eg make  a small /boot partition and format it with ext2. The formatting is important. If The windows installer finds a unformated partition it wants to format it and place some idiotic files like ntldr there...

Or you just delete Windows, like me :-)

---

### Post by drayen on 2008-03-30
Apologies, i know this thread is quite old, but i'm getting a new desktop very soon and i'm very interested in this. 

**My story : **

My new workstation is going to be quite high spec. 
[LIST]
[*]Quad core
[*]4gb ram
[*]2x 500gb SATA disks
[*]GeForce8600
[*]Vista pre-installed
[/LIST]

What i'm thinking of doing / wondering if its possible is 

HD1
[LIST]
[*]0gb->200gb : VISTA
[*]200gb->300gb : (k)Ubuntu / [RAID0]
[*]300gb->500gb : (k)Ubnuntu /home/ [RAID1]
[/LIST]

HD2
[LIST]
[*]0gb->200gb : (k)Ubuntu /downloads
[*]200gb->300gb : (k)Ubuntu / [RAID0]
[*]300gb->500gb : (k)Ubnuntu /home/ [RAID1]
[/LIST]

I also have a media card reader on the system so could have /boot on a 256mb SD card.

Is this possible? My primary aims of this setup are to increase speed and have a real time backup of my work. I understand the risks of Raid0, but feel they are acceptable for applications. 

If (as i hope) this is possible, How would i go about doing it?

Any help/advice/comment are greatly appreciated.

Thanks

Drayen.

---


---
title: "Computer restarting when loading GRUB"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Keldek on 2007-11-28
Hello. Finally have some spare time on my hands and instead of wasting it on MMO's I decided I'd give Ubuntu another go.

First things first, my system setup:

Asrock ALiveNF5-VSTA mobo
AMD Athlon 64 x2 5600+ (socket AM2)
Nvidia Geforce 8800GTS
2GB RAM (DDR2 667 dual channel mode)
2x 250GB SATAII in RAID 0 config (using windows LDM aka softraid)
1x 200GB SATAII as single drive, untouched by windows
Realtec HD Audio (onboard)
Nvidia nForce Network controller


A few other detail:
My BIOS is set to non-RAID
BIOS set to boot from the 200GB single drive


I'm starting a completely fresh build from scratch (zero filled my hdd's, backed up all data on a different comp).


Inititially set BIOS to boot from the first 250GB HDD (please note that in order to change which hdd I boot from, I have to change the actual disk order within the BIOS)
Installed windows on a 10GB partition of the first 250GB HDD (same as boot disk)
Windows did it's thing, installed fine.
Boot into windows and go through my disk layout for the softRAID config
10GB partition on 250GB disk 2 (to match the 10GB windows system partition)
75GB partition on 250GB Disks 1 & 2
100GB partition on 250GB Disks 1 & 2
47.88GB partition on 250GB Disks 1 & 2
Convert both 250GB partitions to Dynamic Drives
Reboot windows and create my RAID 0 based on the partitions above, less the windows system partition & matching 10GB partition on disk 2

Ok, now that the base of Windows is installed, I prepare to installed Ubuntu.

Reboot comp, enter BIOS and set to boot from the 200GB SATA (please note that in order to change which hdd I boot from, I have to change the actual disk order within the BIOS)
Insert and boot to Ubuntu 7.10 Live CD
Start the install
Manually setting up my partition tables on 200GB SATA...
50GB ext3 partition for /
3GB swap
remaining space on 200GB SATA untouched
Before clicking install, I hit the advanced button, taking note that GRUB is installing to hd0
Install goes fine, reboot comp
GRUB menu loads...
Boot into Ubuntu... check
Boot into Windows... check

So it's been a long day, everything seems to be working properly, I hit the rack...

Wake up an hour ago, turn on the comp and here's where the trouble begins...

GRUB goes to load (GRUB Loading Stage 1 something or another quickly flashes on my screen)...
Comp reboots
GRUB goes to Load
Comp reboots

And so the cycle continues endlessly

I enter BIOS, change boot disk to my Windows Disk, save & exit...
GRUB goes to load (why I dunno, it shouldn't have touched this MBR)
comp reboots
GRUB goes to load
comp reboots

Another endless cycle.

So, leaving the Boot order as it is, I wipe & rewrite the MBR on the Windows disk... boot into windows.

A few other details that may or may not help:

Using Ext2 IFS for Windows & Textpad...

/boot/grub/device.map reads:

(hd0)     /dev/sda
(hd1)     /dev/sdb
(hd2)     /dev/sdc

/boot/grub/menu.lst reads (the important stuff):

groot=(hd1,0)

Under 'title   Ubuntu 7.10, kernel 2.6.22-14-generic':
root     (hd1,0)

Under 'title     Microsoft Windows XP Professional':
root     (hd0,0)



So, I'm taking note that GRUB installed itself to (hd0) according to the Advanced options box.
So I'm thinking to myself, "ok self, GRUB installed to the wrong disk... how it initially loaded and I booted into windows/Ubuntu fine last night I'll never know, but it appears that GRUB has indeed installed to the wrong drive."

So I reboot, change my BIOS settings to boot from the 200GB SATA once again; then boot up the live cd, installed GRUB to (hd1), leaving groot=(hd1,0) and root   (hd1,0) as is.

Reboot comp...

GRUB Loading Stage 1...
comp reboots
GRUB loading stage 1...
comp reboots

Endless cycle.

So now I'm here. I apologize for being so long winded on the matter but I wanted to give as many details as humanly possible.

I should also note, not that I think it matters, but just in case:

Before using the Windows LDM to set up my softRAID, I initially tried using my onboard fakeRAID controller. Set up my stripe using SATA 250GB Disks 1 & 2, leaving the 200GB SATA as single.

Go to install Windows, load the proper drivers, install goes fine... then freezes up on the "Installing Devices" portion of Windows install.

Ok, I'm done this time for real :P.

If someone out there in the wonderful land of Ubuntu could help me solve the reboot cycle problem I'm having, I would greatly appreciate it.

Thank you

---

### Post by Keldek on 2007-11-28
anyone out there have any clues as to why this is happening?

---

### Post by confused57 on 2007-11-28
You could try Super Grub Disk to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Do you get the grub boot menu and your computer reboots when you select to boot Ubuntu?

---

### Post by dabl on 2007-11-28
This rebooting phenomenon only happens with Ubuntu?  Does the Live CD work OK?  And Windows runs OK on that hardware?  I'm thinking the problem is related to the RAID, or almost-RAID setup.  Does more than one hard drive have the "boot" flag set on it?

---

### Post by ato on 2007-11-28
I had a gutsy workingon my pc. After a BIOS upgrade on an intel DG965ry my root partition stop working (unknown filesystem).
Now there's no way to install gutsy cause the same problem.

PS
The cd is the same that the previously installation

---

### Post by Keldek on 2007-11-29
> **confused57 said:**
> You could try Super Grub Disk to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Do you get the grub boot menu and your computer reboots when you select to boot Ubuntu?

No, I don't even get to the boot menu. All that happens is "GRUB Loading Stage 1" flashes very quickly on my screen then the comp reboots. I never get to a menu at all.


> **dabl said:**
> This rebooting phenomenon only happens with Ubuntu?  Does the Live CD work OK?  And Windows runs OK on that hardware?  I'm thinking the problem is related to the RAID, or almost-RAID setup.  Does more than one hard drive have the "boot" flag set on it?

Well, I don't think it's an ubuntu thing per say. I never get a chance to even try booting into abuntu because as I said above all I get is a quick flash on the screen of "GRUB Loading Stage 1" then the system reboots.

I can boot into windows just fine (after changing my boot order in the BIOS and deleting/rewriting the windows MBR on that disk. I can also boot into the Live CD just fine as well.

I don't understand why the problem is here considering after I installed Ubuntu and rebooted, the GRUB menu loaded fine and I was able to boot into bot windows and Ubuntu from the GRUB window just fine.

Additionally, I don't see how the problem can be related to the softRAID setup I used in windows, considering I install Ubuntu (and GRUB) to the single disk. The single disk contained no partitions at all and only contains linux partitions currently.

I'm not sure what other info I can give at this moment though as I tried explaining everything in my original post as best I could. However, if I did miss some details let me know and I'll provide the info as best I can.

Thanks again

---

### Post by meierfra on 2007-11-29
Try this. Boot from the Live CD. 

Change "#groot (hd1,0)" in menu.lst  to "#groot (hd0,0)"

(During boot-up, grub names the drive  according to the boot order in the bios, so if you boot from the 200GB drive, the 200GB drive will be (hd0)) 

In a  terminal:

```

sudo update-grub
sudo grub

```

At the "grub>" prompt:
```

find  /boot/grub/menu.lst

```
This will return something of the form  (hdx,y), probably (hd1,0)
```

root (hdx,y)
setup (hdx)
quit

```
(of course replace x and y by their actual values)

Reboot from your 200GB Sata/Ubuntu drive.

---

### Post by Keldek on 2007-11-29
I've given up on trying to get things working properly with the setup I was trying to use... for several reasons.

I'm getting 2 new sata hdd's tomorrow which will go in a raid 1 setup, which also causes me to lose the current single disk as my mobo can only support 4x sata disks. (I'll get a raid controller card eventually though)

So... after a day of trying to fix the endless reboot cycle, I've decided to install windows and ubuntu on a 'fakeraid' setup. After figuring out how to use fdisk from the terminal (and wiping my windows partition several times) I'm finally getting things working how I want.

I'm using this [guide]("https://help.ubuntu.com/community/FakeRaidHowto") to get everything setup in a fakeraid, and so far all is going well. I've read around that some people have had problems installing GRUB to a fakeraid, but hopefully I can overcome that.

Thanks again for the help and I look forward to having things running smoothly soon :)

---


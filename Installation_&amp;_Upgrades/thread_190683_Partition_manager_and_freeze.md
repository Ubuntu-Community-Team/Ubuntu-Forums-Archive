---
title: "Partition manager and freeze"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by bokibre on 2006-06-06
I tried to install with desktop cd, i click on install icon on the desktop and everything was working normally and when i click on manually edit partition and forward paririon manager starts and sart scanning hard disk and everything just freeze!!! I got swap partition of 512MB and blank partition in ext3 of 6GB and 256MB RAM and that partition of 6 GB is made with gnome partitioner with this ubuntu desktop cd!!! Help please!!!!

---

### Post by padre999 on 2006-06-07
exact same issue here... when getting to step 5 and wanting to choose partitions manually, the system freezes while initializing the partitioner...

:???:

---

### Post by padre999 on 2006-06-07
I tried three times now, always the same... ](*,) 

The partition manager window shows up, the partitioner progress bar is moving. Then the system gets first "hickups", i.e. mouse and status bar freeze for a second. Then after 15 secs or so it freezes completely. 

Hardware reset...

I installed with the same CD on my laptop, worked fine. I ran the "Check CD for errors" test, no problems. It is the Ubuntu 6.06 Desktop i386 install CD.
On this system I installed a Kubuntu 6.06 RC1 before without problems.

I am using a Athlon XP system, 512MB Ram, 2 ATA 133 drives  on a ASRock K7S8XE mobo with Sis 748 Chipset.
On the first drive are 2 NTFS and 1 Fat32 partitions. On the second 2 ext3, 1swap and 1 Fat32.

Any help would be appreciated.

Thanks

---

### Post by padre999 on 2006-06-07
as suggested the result of lspci:

```
padre999@Muehle:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0b.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)
padre999@Muehle:~$

```

---

### Post by padre999 on 2006-06-07
I found this bug which fits the description very well:

[https://launchpad.net/distros/ubuntu/+source/espresso/+bug/40464](https://launchpad.net/distros/ubuntu/+source/espresso/+bug/40464)

But it refers to the Beta LiveCD. Why is the problem still there?

---

### Post by bokibre on 2006-06-07
I tried downloading another image but everyting is the same!!!

---

### Post by padre999 on 2006-06-07
[QUOTE=bokibre]I tried downloading another image but everyting is the same!!![/QUOTE]

You mean you downloaded the Desktop LiveCD from another Server? Or did you try with the Alternative CD?

Somebody help please! [-o<

---

### Post by bokibre on 2006-06-07
i downloaded desktop from another server!!! I don't think alternate cd can help us!!! Really somebody help i really want to install ubuntu!!!

---

### Post by padre999 on 2006-06-07
[QUOTE=bokibre]i downloaded desktop from another server!!! I don't think alternate cd can help us!!! Really somebody help i really want to install ubuntu!!![/QUOTE]
The Alternative CD installs without a problem. 8-)   At least on my system.

Much slower then the LiveCD and really ugly, but works.

---

### Post by bokibre on 2006-06-07
and its complete installation??
I have read that it is used for update etc.???

---

### Post by padre999 on 2006-06-07
[QUOTE=bokibre]and its complete installation??
I have read that it is used for update etc.???[/QUOTE]

The Alternative CD installs the same as the Desktop CD. Did a fresh install on my Desktop PC. I am writing from that system now... 

It is simply no LiveCD, has a ugly text based installer interface and is a bit slower in the installation process as I wrote before. The problem we have has to do with the graphical Partitioner from the LiveCD I think. Made already lot's of problems in the Beta stage, erasing partitions etc...

Try the Alternative CD.

Good Luck

---

### Post by penguinfan on 2006-06-07
Same here, somebody pls get a solution:???: 

Asus L3H laptop, 2gig cpu, 256mb ram, shared Sis graphics, dual boot with XP on hda1.

---

### Post by danyulo on 2006-06-07
Same problem here on Athlon64 installing from the latest CD.
Freezes on choosing partitions screen.

Are the developers aware of this issue?

---

### Post by Caraibes on 2006-06-07
Same here, I am writing from the new Dyne:Bolic 2.0 live-cd, since I could not install Ubuntu and Kubuntu on my Via 796Mhz procesors...

I guess I'll have to download the alternate version...

It's amazing how many bugs and problems showed up in that Dapper who was supposed to be the final solution against M$...

Anyway, no hard feelings, and I can only encourage the works of developpers...

8-)

---

### Post by bokibre on 2006-06-07
I had previous versions of ubuntu installed so that instaler is familiar to me!!

---

### Post by gborzi on 2006-06-10
I have had a similar problem on my AMD64, which has an Asrock 939S56M. The partitioners didn't freeze, they did nothing. Both gparted, fdisk and the text install "seems" to work, I made the partitions, write them to disk, reopen the partitioner and nothing was written ](*,)  .
I solved this problem in the BIOS, by disabling the "Block mode" for the first IDE channel, and unplugging the power. I'm not sure, but it seems that if you don't unplug the BIOS doesn't change :-k . Damned asrock Motherboards ...
Now I have another problem with the nvidia drivers.

---

### Post by dynnamitt on 2006-06-11
...and even I have the same problem!  Freeze freeze freeze.

Im using a Fujitsu Siemens E Series Lifebook. E8020.

Cannonical should release a new Dapper ISO , shouldn't they ??? :confused: 

THIS BUG MUST BE FIXED ASAP!! 

..this post is from the Live part of the Desktop CD.

---

### Post by dynnamitt on 2006-06-12
..could there be hope:

[https://wiki.ubuntu.com/DapperPointReleaseProcess](https://wiki.ubuntu.com/DapperPointReleaseProcess)

I just tried the Alternate CD ..and even that one freezes.

The only way to install a fresh Dapper for me is to first install 5.10 and do a update..............:confused:

---

### Post by Ulinux23va on 2006-06-12
Xubuntu installer freezes if I select the option to Manually Modify the partition table (Step 5 of 6). However, it will install correctly if I let Live CD reformat the ENTIRE disk. I do not want to do this since I have a Win 2k partition in it.

My system configuration is Pentium III 667 MHz, 128 MB RAM, 60 GB Disk 1 and 7 GB disk 2

Any help/suggestions appreciated.

---

### Post by polpak on 2006-06-12
I have the same issue. I had to use the alternate installer in order to get it working. Tried several times. Always locked up on step 5 of six after going through the manual partition process.

---

### Post by bokibre on 2006-06-12
alternate cd worked for me!!!

---

### Post by 111787 on 2006-06-12
Try 'Safe Graphics Mode'.  It solved the problem for me.

---

### Post by Ulinux23va on 2006-06-13
I downloaded alternate install CD and burned it at 4x (apparently it makes a difference). I was able to install xubuntu in the second partition now. 

The screen size is not what it should be (I have seen this issue being raised elsewhere) and couple of other things needs to be fixed (downloaded new packages like Kontact, kmail, evolution now I cannot login - problem with kthemes). So far I have spent 3 solid days (and counting) to get it to work the way I want it.

Currently doing 4th (or is it 5th....) CLEAN install. This is fun....

---

### Post by kaede on 2006-06-26
i do have the same problem with freezing clause. does anybody now how to fix it? in the end it makes my windows partition broken. 

i'm installing with text mode. is there any diferent with using safe graphics mode?

---

### Post by lhyasia on 2006-11-09
Same problem. 

My computer: P4 2.6GHZ/256MB RAM/80GB HDD/DVD. (winXP + FC3)

3 days before, i found the liveCD internet, last night i got
it, it looks nice. liveCD boot, load system, ran desktop ok, 
cool UI! then i obey the install instruction, click the install
icon to perform install procedure....

step 1-5 are good, although step 5 a little slow, and i select 
1GB swap and 10GB ext3 for linux, but trouble come when step 6,
installer freeze at progress 34%, 15 minites later, i let the 
PC hard reset, and bigger trouble, I cannot see my Graphic grub,
i got a grub command line prompt, it seems i have lost my XP 
partition? 

i try 3 times, but all freeze at step 5, partation manager cannot 
work normally!!  last night i did nothing except enjoy the freeze
progress bar. and 3 times system hardware reset!!

](*,) ](*,) ](*,) 
Evil installer, Evil liveCD, or Evil my poor PC?

---

### Post by Sef on 2006-11-10
Have you tried the alternate cd?  It often works where the Desktop CD fails.

---

### Post by Dacky1 on 2006-11-10
Does the Alternative CD give the same end results as the desktop CD? I don't want to install it and it be totally different from Ubuntu 6.06 lts dapper desktop livecd.

---

### Post by frizzl on 2006-11-11
sigh, my install disc (6.10) was working last week, now it's having this problem :(

i was having this problem with 6.06, and was so happy when it was gone in 6.10 but has somehow REAPPEARED :S

---

### Post by vintendo on 2006-11-11
When I try to install from the 1st option it freezes at the partion step. And when I boot from Safe Grafix mode it freezes and some times I cant even boot from the safe grafix option, it'll jut freeze at that. ](*,)  i cant try the alternitave cd cuz i thought this install of ubuntu was gonna be a breeze (silly me huh) And now im left with no XP to dl the Alternative cd with. The Edgy Cd that I first downloaded, I got it from the servers and it wouldnt even boot. So then i went to torrentspy.com and I got the CD from there And now it wont install :( ](*,)  Why is this so difficult to do? ]:confused: (*,)

---

### Post by vintendo on 2006-11-11
I managed to get to step 6/6 and the pc froze at 15% :(

---

### Post by h-bar on 2008-03-22
I am having the same problem - downloaded live CD from bitTorrent, burned (if 4x makes such a difference, someone should put it in the wiki), reboot, works fine until after step 5, window pops up saying "starting partition manager", mouse spins, spins, spins, stops.  Hardware reboot.

First time I tried, it was with Heron beta, downloaded Gibbon, same exact problem.

Tried just LiveCD, worked fine until I tried the hardware checker, same problem on sound card check.  Ran the check-CD function, no errors.  Ran memory check function, no errors.  First time with linux, I really would like this to work

P4 2.8Ghz Northwoods
2 GB (4x 512MB) DDR
3x HDD: 37 GB 7,200RPM WD (SATA, NTFS), 120 GB Seagate (IDE, FAT32), 360 GB WD (SATA, NTFS)
Lite-on CD-RW/DVD
SB Audigy 2 (PCI)
GeForce 7800 GS (AGP)
US Robotics wireless card (PCI)

---


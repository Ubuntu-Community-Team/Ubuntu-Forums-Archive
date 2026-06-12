---
title: "Ubuntu + WinXP paritions"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by kkarim on 2006-11-24
Hey..
I have two laptop HDD. One is 80gb one is 40gb.
I had Fedora-WinXP on dual boot on my old 80gb but wasn't conviced to switch to completely linux with fedora. 
I decided to try ubuntu, so i put in my 40gb hdd just to install ubuntu on it. I was gonna remove fedora and install ubuntu if i liked it. That was 6month ago. Ubuntu got to me then and i forgot about my spare drive with winxp fedora on it.
Today i decided to reformat it, and install WinXp and Ubuntu on it, since i still use windows (only for itunes/ipod support, this is the only thing where i couldn't find a viable alternative) i use a VWware winxp guest for the other apps i need windows for (Matlab, CodeWarrior... etc)

I have an 80gb i need to partition in order to:
-have a big enough fat32 parition for music and picture that will be set to "My Documents in windows" and mounted under smtg in linux
-have a home partition for ubuntu
-have a "/" in linux
-have a partition for winxp
-have about 2gb of swap for windows..

I still can't decide on how to spread them.. :/ Any help would be apreciated.. :) Sorry for the long post :)

---

### Post by cilynx on 2006-11-24
What I would do:

20G NTFS:  Install WinXP, Matlab, CW and have 2G open for swap
19G EXT3:  Install Ubuntu and all your cool aps
01G SWAP:  You won't use 1G of swap within the technological lifetime of this machine
40G FAT32: Shared Media Storage

Unless you're really expecting to kill the drive, there's no reason to split / and /home on your Ubuntu setup.  If you do, you risk running out of room on / as time goes on.

Just my $0.02

---

### Post by kkarim on 2006-11-24
iTunes too will be installed on windows.

i liked using VMware for matlab and CW on Ubuntu.. Don't need to reboot.. the only pain in the *** is my iPod and it's honestly the only reason that's making me reinstall windows.

I am currently thinking of buying a power supply for an old laptop i have and using only for the ipod.. dedicating my current laptop for ubuntu..
I'm lost..

:confused:

---

### Post by cilynx on 2006-11-24
You can VMWare your way into the same WinXP setup that you boot into.  I did it when I needed Xilinx and Multisim.  I booted Win for C&C and VMWared the same WinXP install for Xilinx and Multisim.

Have you looked into the iPod mungers on Ubuntu?

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)
[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)
[http://www.quietglow.com/docs/ubuntu5gpod.html](http://www.quietglow.com/docs/ubuntu5gpod.html)

---

### Post by kkarim on 2006-11-24
> **cilynx said:**
> You can VMWare your way into the same WinXP setup that you boot into.  I did it when I needed Xilinx and Multisim.  I booted Win for C&C and VMWared the same WinXP install for Xilinx and Multisim.

Have you looked into the iPod mungers on Ubuntu?

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)
[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)
[http://www.quietglow.com/docs/ubuntu5gpod.html](http://www.quietglow.com/docs/ubuntu5gpod.html)

I looked into ipod manager and tried them all... i just like the connect it and let it do its job itunes provides me.. :P

Do you have a guide on how to vmware the same winxp i boot into?? that would be very helpful for me. 
Thanks a lot..

---

### Post by cilynx on 2006-11-24
It's not all that complex to "dual boot" one WinXP partition.  You install in the real world and make sure that it works well.  You then fire up VMWare Server (Not Player) and make a new virtual machine.  You tell it to "use a whole partition".  I think they call it "expert mode" or something.  You just point it at your XP partition and hope.  It should just work.  It'll run you through the whole "found new hardware" jack from the install again, but only the first time.

---

### Post by kkarim on 2006-11-24
hah that's much easier than i though. I can't try that now since i don't have XP installed on my current machine. I'll try it for sure later though, i really like the idea. :)

BTW: the more i use linux, the less i like using windows.. :P

---


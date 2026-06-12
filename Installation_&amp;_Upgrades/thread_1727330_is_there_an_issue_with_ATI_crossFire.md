---
title: "is there an issue with ATI crossFire"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by valugi on 2011-04-12
I bought myself a new (nice) piece of hardware.
> 
Processor : AMD PHENOM II X6 1055T 2.80GHZ C6 AM3 RET
HDD: SEAGATE 1TB SATA2 7200RPM 32MB CACHE
Power: LSP750	 750W POWER SUPPLY
Memory : 16 GB 4GB DDR3 1333 PC1060
Mainboard : ASUS M4A79T DELUXE	 AM3 4X16XFRX 4D3 16 1GL R ATX
Video : 3 x GIGABYTE RADEON HD5750 1GD5 XFRX VGA 2DVI HDMI in Crossfire


Of course it comes with Windows7 and I want to fix this problem. Main thing is that I want to keep Windows7, just because I like to play Starcraft2.
So I tried to install Ubuntu 10.4 next to win. Unfortunately the first time I tried it crash during the install. It ruined the partitions and I could not see half of the disk so I had to enter with the live CD and use the disk utility as detailed [here]("http://askubuntu.com/questions/33973/incomplete-install-and-i-cannot-see-part-of-the-hard-disk"). This problem solved I tried to install a new copy of 10.10 64bit. I enter the install process I start manual partitioning and the system freezes. Not at a specific point, it happens in various moments. But constantly freezes. Finally I gave up with Ubuntu and tried the latestes of openSuse. Their install process was a little more elaborate and I succeeded in installing but nevertheless it seems there a problem. Whenever I got into Suse it freezes after a number of minutes. No exceptions. So I guess that maybe is something common both to Ubuntu and Suse.
The first thing that poped into my mind as a potential problem is the Crossfire and from here the title of the post.

I really want to have my developing environment so please help with suggestions. I'll try to provide logs, dumps or whatever other things you need.
Thanks


UPDATE
I succeded in installing ubuntu 10.10 following advice from **PCNetSpec** from this [post]("http://ubuntuforums.org/showthread.php?t=1724836"). Nevertheless it frozed on updates before allowing me to install the ATI driver. The same happend with Suse. After trying to update I cannot connect even in safe mode. I dont know if is the mainboard all the combination of mainboard and videocards, but are not properly tested under linux so I wont recommend them to anyone yet.

UPDATE 2
Deleted everything and tried again. 
It appears that while booting in linux, the ventilator speed keeps rising until a point that it freezes, even in the installer or when running a live CD. 
Could this be a memory issue or a mainboard issue?

UPDATE 3
I removed 2 of the 3 video cards and the install went ok. It seems that the crossfire and Ubuntu are not friends yet.

---


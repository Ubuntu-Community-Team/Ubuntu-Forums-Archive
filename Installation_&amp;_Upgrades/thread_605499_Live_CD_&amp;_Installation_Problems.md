---
title: "Live CD &amp; Installation Problems"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by ianpallen on 2007-11-07
Hi,

This is my 1st post here and well I've currently got no experience with ubuntu but I would very much like to use it instead of XP, but I'm having 2 problems..

1. When I use the Live CD for "Ubuntu 7.10" I insert the CD and it seems to go through the loading process but when the desktop appears the display is awful - it's like the whole screens is flickering and I can't see anything.

2. After the above problem I decided to make a Live CD for "Ubuntu 6.06 LTS" this loads fine and there are no display problems but, when I try to do an install it gets as far as the partitions but it can't find anything, I have 2 partitions - one with XP on it (c:) and one with nothing on it (e:) 

So what am I doing wrong?

Thanks.

---

### Post by ajgreeny on 2007-11-07
What hardware have you got?  It sounds as though your graphics is letting you down.  Try disabling all the desktop effects if they are activated on your machine,  System>Preferences>Appearance and on the Visual Effects tab chose "None".  That may help but if not come back with more info and someone may be able to help you more.

---

### Post by ianpallen on 2007-11-09
It's actually my sisters PC so I'll post the specs when I go there later on today, as for turning the effects off, I can't see any part of the screen at all clearly so I wouldnt be able to find those controls anyway.. any ideas on the other part of my question where the installation can't find a partition to use?

Thanks

---

### Post by bulldog on 2007-11-09
Maybe you should download the alternate cd.
This one is text based install,what is basically the same as with the live cd,but you won't have a desktop loaded.

Check the green box and download it

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by ianpallen on 2007-11-09
Thanks i'll give that a go later on.

---

### Post by ianpallen on 2007-11-09
Well I tried the alternate cd and near the end I got a message saying grub installtion failed, then when ubuntu loaded up I got the usual flickering and when I tried to change effects the system seamed to lockup..

The system is as follows: -

Pentium 4 Based Processor
1gb ddr ram
No Video Card
Abit SG-95 Motherboard

When I installed XP previously I rememeber I had to download and install drivers for the display, usb and lan card. So is it possible theres an issue with ubuntu and the motherboard?

I should also say that the reason for trying ubuntu is that the xp install was giving me blue screen errors alot. I'm guessing theres some kind of hardware problem.

Thanks

---

### Post by bulldog on 2007-11-09
If you have no graphics card,how do you want anything displayd at your screen?
You have probably a onboard graphics chip,it could be handy to know what kind of chip this is.

---

### Post by ianpallen on 2007-11-09
Yeah it's onboard graphics, heres the spec for the board: -

• High performance ABIT Intel series integrated motherboard
• Supports Intel Conroe Processors / Pentium® 4 & Celeron® & Celeron® D CPUs
• Designed for Intel LGA775 processors with 800MHz FSB
• Supports Intel® Hyper-Threading / EM64T / EIST technology
**• Integrated SIS Mirage™ 1 Graphics GPU with high performance 256-bit 3D engine and 2D accelerator**
• Supports DDR2 667/533 memory
• On-board 10/100 LAN for networking and broadband
• On-board 7.1sSurround-sound HD Audio
• 1 x PCI-E X16, 1 x PCI-E X 1, 2 x PCI
• 2 x SATA 1.5 Gb/s RAID connectors
• 2 x Ultra DMA 133/100/66/33 IDE Connectors
• 4 x USB 2.0 ports

---

### Post by ianpallen on 2007-11-12
any ideas?

over the weekend I got Partition Magic and made an Ext3 partition, but when I go to install ubuntu 6.06 it still can't find any partitions.. I think I'm gonna start to pull my hair out soon..

---

### Post by ianpallen on 2007-11-15
Well I've now put another hard drive in and the partition manager can see the new 1, that does what it needs to do and installation starts, however I get to %15 and it stops, I've left it like that for over an hour and still nothing... what should I do?

Thanks

---

### Post by bulldog on 2007-11-15
First of all,don't use PM to make linux partitions,they won't go well together.
Use GParted live cd instead,to make your partitions.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

How you many partitions you want to make is up to you.
Some suggestions though,
Create 10GB for /
Create 1-2GB for swap
Create a partition for /home as big as you want.

When you come to the partition part,choose manual.
Mount the 10GB as /  format  ext3 and set bootflag enable
Mount swap as swap format as swap
Mount last partition as /home format ext3 
Apply changes and proceed with the install.

---

### Post by ianpallen on 2007-11-15
I'll try that thanks.

---


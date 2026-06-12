---
title: "Installation of Ubunto 10.04 on second internal HD"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by wittzi on 2010-09-08
Hi All,

This is my first post and whilst I have seen *similar* posts I need to be 100% sure about this as I am desperate not to frag my Windows 7 installation.  Any advice you have would be gratefully received!

I have 3 physical disks; 40Gb SSD, 750Gb SATA, 250Gb SATA

Win7 is installed on the SSD drive and I use the 750Gb drive as my data drive.  The 250Gb drive is free and therefore I want to install Ubunto as a secondary (but hopefully one day primary!) OS.  Having just completed a VMWare course I want to become more familiar with Linux.

Anyway, I run the LiveCD and select install and as expected, it detects that Win7 is installed and asks if I want to run them side by side.  Of course I do, but it seems that in order for me to do that I need to use the 40Gb SSD (partitioned) which I can't do as it's nearly full.

I am able to select the 250Gb drive by clicking on the second radio button from the installer which is great, however this involves me selecting a standard installation option and shying away from the original option which specifically states that it will install Ubunto alongside Windows 7[I].

[/I]I fully understand that if I just select this option all will probably be well, but I want to be sure that this is the case as I cant afford to be without Win7 as I need it for VPN access with work and for my beloved games!  ;)

Having used to the LiveCD to check out Ubunto (and have written this post using the Firefox browser on the LiveCD) I'm itching to use the operating system properly!

Thanks in advance,
WittZi

---

### Post by lisa374 on 2010-09-08
The way I did it, with a new second drive, was to select use hard drive, not side-by-side.
Then, selecting the correct hard drive, just went through the default selections.
Side by side puts Ubuntu on the same drive as your first OS. Obviously you don't want this. Thus the only options left are use new hard drive (btw you will loose all data) or manual partition. Again, choose the middle selection. Your mileage may very. Took me three tries to get the correct buttons pushed.

---

### Post by oldfred on 2010-09-08
Welcome to the forum.

Along side means on the same drive and it will auto shrink the existing partition (if it can).

You just want to install to a second drive. Besure to use the advanced button to know where grub gets installed. You will have to decide if you want to boot thru the SSD and put grub on that drive or on the 250GB drive. I prefer to have grub on the same drive as the Ubuntu install.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

I prefer to use gparted and set up partitions in advance, so I know sizes, formats and locations. Then use manual install to choose which partitions to use. You have to use manual if you want a separate /home although now you can set up partitions as part of the install.

Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I like to have several / (root) partitions so I can experiment with new versions or other systems. Since you only need 20 or 25GB for a generous root partition (if you have data elsewhere) you can have a lot of system installs in 250GB if you want to experiment.
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

---


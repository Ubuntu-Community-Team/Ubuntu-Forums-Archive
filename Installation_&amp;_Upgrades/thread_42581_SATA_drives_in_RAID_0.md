---
title: "SATA drives in RAID 0"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Gudrune on 2005-06-18
I tried out the live CD and was pretty impressed with Ubuntu. I figured I would install i but I'm worried about the partition part. 

The installer gives me an option to format install on SBA (I may bee off on the SB part) or B both are 160GB. Is that one harddrive or is it recognizing my current setup I have windows on C and storage partition D both split 160GB I have two 160GB hard drives in RAID 0

I don't want to mess up my RAID and lose windows (for now)

Thank and hope that made any sense.

Asus A7N8X Deluxe Motherboard
Silicon Image Sil 3112A Controller

---

### Post by bluesman2333 on 2005-06-18
[QUOTE=Gudrune]I tried out the live CD and was pretty impressed with Ubuntu. I figured I would install i but I'm worried about the partition part. 

The installer gives me an option to format install on SBA (I may bee off on the SB part) or B both are 160GB. Is that one harddrive or is it recognizing my current setup I have windows on C and storage partition D both split 160GB I have two 160GB hard drives in RAID 0

I don't want to mess up my RAID and lose windows (for now)

Thank and hope that made any sense.

Asus A7N8X Deluxe Motherboard
Silicon Image Sil 3112A Controller[/QUOTE]

As far as I know, the part of the installer that does the RAID is completely borked up. I screwed with it for quite a few hours and gave up on Ubuntu and RAID. I have four 250 GB HDD's and couldn't get the RAID installer to work no matter what I did.

---

### Post by alastair on 2005-06-18
RAID install works FINE.

BUT - you will probably NOT be able to install on a "h/w" RAID setup because a Linux driver will not be available. THis is not normally a problem - Linux has good s/w RAID support anyway (and the cheaper "h/w" RAID cards are essentially s/w RAID anyway. But if you already have a RAID setup for Windows - then you probably cannot install Ubuntu on the RAID without affecting Windows,

If you have TWO disks (e.g. sda,sdb), you can easily partition each identically in Ubuntu install, and setup s/w (md) RAID - and install on Linux s/w RAID.

---

### Post by Gudrune on 2005-06-18
Installation shows both sda,sdb. I have a ton of stuff on windows with raid already set up. Don't feel like wiping it to run linux. Kinda surprised SATA and RAID 0 is still hard to do with this motherboard. It far from top of the line these days.

Maybe someday in the future  :???:

---

### Post by piers on 2005-06-19
Hi, we are currently in the process of building a new mail server and are trying to decide whether to use Ubuntu or Windows. The only thing stopping us from using Ubuntu is knowing whether or not we can *easily* set up RAID 0+1 using a real hardware raid controller. I have been looking at the aec6896 card from ACard but i am unsure if i need to install any drivers for the 4 SATA drives to be recognised as one? ](*,)
I have been searching the net for days and am becomming blinded by specifications and contradictory reports! please please can someone point me in the right direction or offer definate advice?
Thanks in advance

---

### Post by Ab3 on 2005-06-30
[QUOTE=piers]Hi, we are currently in the process of building a new mail server and are trying to decide whether to use Ubuntu or Windows. The only thing stopping us from using Ubuntu is knowing whether or not we can *easily* set up RAID 0+1 using a real hardware raid controller. I have been looking at the aec6896 card from ACard but i am unsure if i need to install any drivers for the 4 SATA drives to be recognised as one? ](*,)
I have been searching the net for days and am becomming blinded by specifications and contradictory reports! please please can someone point me in the right direction or offer definate advice?
Thanks in advance[/QUOTE]

I sucessfully setup ubuntu with full Raid-1 using a 3ware Sata h/w raid controller. Basically u need an Os independent raid controller for it to work with Ubuntu. I had problems getting the s/w raid working completely, would appreciate it if one of you who got it working successfully could post detailed instructions for others.

---


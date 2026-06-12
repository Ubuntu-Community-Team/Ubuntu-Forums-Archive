---
title: "can not run ubunto ! :("
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by mehhraan on 2011-12-07
Hi guyz 
first I'm sorry cos I'm just starting to learn english and I pretty much suck at it :o

here is my problem with ubuntu : 
I downloaded Wubi 11.10 with ubuntu-11.10-desktop-i386.iso then I installed it . when I reboot it went to ubuntu to countinue installation but nothing happens after minutes ! so I went back to W7 and unistalled it and then installed it again and when it went for countinue installation I pressed ESC and choose safe graphic or something like that and everything was perfect and I successfully install ubuntu and it rebooted . but when I choose ubunto I have 2 option : normal and recovery mode . I press normal mode and then there is some text like testing battery and ... ! and nothing happens ! and same thing in recovery mod as well , I press ctrl+alt+f2 and it ask s for user and password and I'm writing it and type sudo dpkg-reconfigure xserver-xorg but nothing happens ! I unistall and install it 2 more times but still have the problem ! 

any suggestion ? 

Thanks in advance :o:P:D:)

---

### Post by mehhraan on 2011-12-07
I have multiple hdd s but not raid !  C drive is a  hard drive with 1 partition 465G and about 390G is free with windows 7 sp 1 on it 

Cpu : quad core q9550 - 4g ram 1066 . Nvidia 295GTX (not overcloke mode !)

---

### Post by mehhraan on 2011-12-07
even ubuntu live freezes ! 
I think there is something wrong with my NVIDIA card ... I tried 4 different HDD with lots of different partitions !

---

### Post by oldtimer7777 on 2011-12-07
> **mehhraan said:**
> even ubuntu live freezes ! 
I think there is something wrong with my NVIDIA card ... I tried 4 different HDD with lots of different partitions !

Skip using Wubi for now, and try to boot from a Live Bootable USB Flash Drive of Ubuntu 11.10.  You can build one with instructions on this page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Use option two, and read the instructions on how to create a Ubuntu 11.10 USB Flash Drive that you can test your system with.  You'll be able to boot directly from that USB Flash Drive and you can see if your hardware is compatible and if it works or not.  If so, you can install Ubuntu at that point from the USB Flash Drive onto your computer HDD. Installation from a USB Flash Drive only takes about 15 minutes tops.

If you want to install Ubuntu from your Flash Drive, here is a guide:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by MAFoElffen on 2011-12-07
> **mehhraan said:**
> Hi guyz 
first I'm sorry cos I'm just starting to learn english and I pretty much suck at it :o

here is my problem with ubuntu : 
I downloaded Wubi 11.10 with ubuntu-11.10-desktop-i386.iso then I installed it . when I reboot it went to ubuntu to countinue installation but nothing happens after minutes ! so I went back to W7 and unistalled it and then installed it again and when it went for countinue installation I pressed ESC and choose safe graphic or something like that and everything was perfect and I successfully install ubuntu and it rebooted . but when I choose ubunto I have 2 option : normal and recovery mode . I press normal mode and then there is some text like testing battery and ... ! and nothing happens ! and same thing in recovery mod as well , I press ctrl+alt+f2 and it ask s for user and password and I'm writing it and type sudo dpkg-reconfigure xserver-xorg but nothing happens ! I unistall and install it 2 more times but still have the problem ! 

any suggestion ? 

Thanks in advance :o:P:D:)
Suggestions? 
- First, once your get it reinstalled from either Wubi or traditional- Stop and take a breath...

Do you have ATI Radeon or Nvidia Graphics? Most likely = Yes.  The hang at "Checking Battery State" is usually that you don't have your graphics drivers loaded or that they are not configured.

What you need to do is use a recovery boot item to go in, use safe graphics/low graphics mode... to boot into the desktop > go to System Settings > Additional Drivers > Install the driver for your graphics card.

Otherwise this is done via Grub and using a nomodeset to boot...

If you knew your video card, I could tell you how to install from the CLI. Or while you are at a prompt, post the results of
```

lspci -vnn | grep VGA

```

---

### Post by bcbc on 2011-12-07
For instructions on supplying nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Wubi specific instructions in post #8

---

### Post by mehhraan on 2011-12-08
> **oldtimer7777 said:**
> Skip using Wubi for now, and try to boot from a Live Bootable USB Flash Drive of Ubuntu 11.10.  You can build one with instructions on this page:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Use option two, and read the instructions on how to create a Ubuntu 11.10 USB Flash Drive that you can test your system with.  You'll be able to boot directly from that USB Flash Drive and you can see if your hardware is compatible and if it works or not.  If so, you can install Ubuntu at that point from the USB Flash Drive onto your computer HDD. Installation from a USB Flash Drive only takes about 15 minutes tops.

If you want to install Ubuntu from your Flash Drive, here is a guide:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **MAFoElffen said:**
> Suggestions? 
- First, once your get it reinstalled from either Wubi or traditional- Stop and take a breath...

Do you have ATI Radeon or Nvidia Graphics? Most likely = Yes.  The hang at "Checking Battery State" is usually that you don't have your graphics drivers loaded or that they are not configured.

What you need to do is use a recovery boot item to go in, use safe graphics/low graphics mode... to boot into the desktop > go to System Settings > Additional Drivers > Install the driver for your graphics card.

Otherwise this is done via Grub and using a nomodeset to boot...

If you knew your video card, I could tell you how to install from the CLI. Or while you are at a prompt, post the results of
```

lspci -vnn | grep VGA

```

> **bcbc said:**
> For instructions on supplying nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Wubi specific instructions in post #8

tnx a lot guyz . you're great :)

with ur helps now I'm running ubuntu in live . I want to install it now but I have a problem . I have two internal HDD
HDD no.1 : is seagate 500GB with a primary partition 
HDD no.2 : is samsung 1TB with two logical partition . 731GB and 200 GB 

I want to install ubuntu right now but I'm stuck in Ready when u ... or something like that 

by the way I choose install alongside window 7 and I drag the divider and make ubuntu size 100GB 

my question is:  is it good to make a new partition or there is a better option for having windows7 alongside ubuntu

tnx again :KS

---

### Post by yndesai on 2011-12-08
You will surly need an additional partition to install ubuntu for the file system is not FAT/NTFS. You can safely install ubuntu in space as low as 4GB but I would recommend 20 Gb. 

Create space and partition using "gparted" provided in the live CD and avoid the HDD on which windows 7 is install create the partition in the other HDD (just for safety.

---

### Post by mehhraan on 2011-12-08
> **yndesai said:**
> You will surly need an additional partition to install ubuntu for the file system is not FAT/NTFS. You can safely install ubuntu in space as low as 4GB but I would recommend 20 Gb. 

Create space and partition using "gparted" provided in the live CD and avoid the HDD on which windows 7 is install create the partition in the other HDD (just for safety.
done !
tnx man . I didn't lose any data. although grub is not my default boot loader and windows boot manager is default but I configured it with easyBCD 

but again ubuntu in normal mode freezes ! where is this safe graphic mode ? I had that in installation progress but I don't have it now ! 


this forum kicks *** ! thanks for all ur helps :guitar:

---

### Post by mehhraan on 2011-12-08
> **mehhraan said:**
> 

but again ubuntu in normal mode freezes ! where is this safe graphic mode ? I had that in installation progress but I don't have it now ! 


this forum kicks *** ! thanks for all ur helps :guitar:
I wrote some code like kgdp-reconfigure xserver-xorg and xforcevesa and in safegraphic mode it didn't freeze so I installed the geforce driver and everythink works absoluetly perfect 

problem solved 
thanks again :KS

---


---
title: "Ubuntu Installation gone wrong"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Ang98230 on 2011-05-04
I just dusted off my old Compaq Prezeio 900Z. Unfortunately, when I try to install Ubuntu, it screen freezes on me and the computer restarts. Help Please.

---

### Post by dino99 on 2011-05-04
follow this help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by tommcd on 2011-05-04
What are the specs of this computer (CPU, motherboard chipset, memory, and graphics)?
What version of Ubuntu are you trying to install?
How did you burn the Ubuntu CD?
Did you check the CD for defects?

You need to provide more info here.

And welcome to the Ubuntu forums!

---

### Post by Ang98230 on 2011-05-04
The specs for my laptop are Standard Features
> 14.1" TFT XGA Display
> AMD® Mobile AthlonTM XP 1500+
(1.33 GHz1) - with PowerNow!TM
Technology
> 256KB L2 On-Chip Cache
> 256 MB 266 MHz DDR SDRAM,
upgradeable to 1.0 GB
> 20.0 GB2 Ultra DMA 4200 RPM
Hard Drive
> 8X DVD/CD-RW Combo Drive3
> 56K ITU V.92 PCI4
> Integrated 10/100 Base-T Ethernet Port
> ATI RadeonTM IGP Integrated Graphics
> JBL Pro Performance Audio with Bass
Reflex
> High-capacity Li-ION Battery
Graphics
> ATI RadeonTM IGP Integrated Graphics
> 16 MB shared video memory
> Maximum internal resolution of up to
1024 x 768 x 16M; with external monitor –
1600 x 1200 non-interlaced
> 32-bit color provides up to 16M brilliant
colors
> Video Player (AVI, MPEG2 and others)
> S-Video TV-Out
> MPEG2 full-motion video playback
Audio
> JBL Pro Performance Audio with Bass
Reflex
> Ported bass reflex enclosures
> Compaq DVD Player/Navigator
> Audio CD Player with control function
keys (Play/Pause, Stop, Previous Track,
Next Track)
> Digital Volume Control
> PCI Audio
Software
Preinstalled
> Microsoft® Windows® XP Home Edition
> Microsoft® Works 6.0
> Microsoft® Money 2001
> InterVideo WinDVD

I was attempting to run Ubuntu 11.04 and I burned the disk using Windows 7. I have not checked the disk for defects however.

---

### Post by ivanovnegro on 2011-05-04
If I saw it right, you have only 256 MB of RAM, thats not really enough to run Ubuntu 11.04.
You should run another version, I would really suggest to upgrade your hardware if you want a good experience with the newest Ubuntu release, and also 1 GB of RAM would not be satisfying for me.

---

### Post by elewis on 2011-05-04
You might consider xubuntu which is the XFCE version of Ubuntu. XFCE is a quite a lot more 'light weight' desktop environment. I find XFCE runs on older weaker computers that will not run Ubuntu or Kubuntu, the KDE version. Check out [http://www.xubuntu.org](http://www.xubuntu.org) and [http://www.xfce.org](http://www.xfce.org)

---

### Post by ivanovnegro on 2011-05-04
> **elewis said:**
> You might consider xubuntu which is the XFCE version of Ubuntu. XFCE is a quite a lot more 'light weight' desktop environment. I find XFCE runs on older weaker computers that will not run Ubuntu or Kubuntu, the KDE version. Check out [http://www.xubuntu.org](http://www.xubuntu.org) and [http://www.xfce.org](http://www.xfce.org)

Or maybe Lubuntu as 256 MB is also really poor for Xubuntu.

---

### Post by tommcd on 2011-05-05
I would go with Lubuntu also. Xubuntu is not really that much lighter on resources than Ubuntu.
You can also do a minimal install of Ubuntu: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
As others have said, upgrading the memory would make the system much more usable. 1GB of memory would be the "sweet spot" in terms of the best bang for the smallest investment.

---

### Post by Ang98230 on 2011-05-05
Thanks guys, and i found out that Xubuntu doesn't work that well either. So off to get Lubuntu!

---

### Post by Dutch70 on 2011-05-05
Yes, the recommended amount of RAM for Xubuntu is 512MB. 
Lubuntu should run fine on 256MB of RAM. 
It's surprisingly nice for old computers if you can't add more RAM right now.

---

### Post by Ang98230 on 2011-05-08
So i have now tried Ubuntu, Xubuntu, and Lubuntu and after i start up each one, it will reboot and after, each system is rendered unbootable, and a gfxboot failure is to blame. What is causing this?:confused:

---

### Post by tommcd on 2011-05-11
> **Ang98230 said:**
> So i have now tried Ubuntu, Xubuntu, and Lubuntu and after i start up each one, it will reboot and after, each system is rendered unbootable, and a gfxboot failure is to blame.
Are you able to run Lubuntu from the Lubuntu live CD? Does the live CD crash at all?
Boot up the Lubuntu live CD and run the option to check the disc for defects. This will insure that you are at least starting out with a valid installation CD.
What exactly happens when you boot Lubuntu after you install it? How do you know that a "*gfxboot failure is to blame*"?

---

### Post by Ang98230 on 2011-05-12
Sorry about all these troubles, im new with Ubuntu. Anyways i'll try to attach a .jpg, but i cannot check the disk for defects, as i cannot pass one of the load screens.

---

### Post by Dutch70 on 2011-05-12
You need to check the md5sum of the .iso that you downloaded. There is info on this page.
[[COLOR="RoyalBlue"]http://lubuntu.net/[/COLOR]]("http://lubuntu.net/")

You also need to make sure that you're burning the disc at the slowest speed possible. If it still doesn't work, try a different brand of cd's, or a different burning program.

The best way IMHO is to use a usb stick aka flash/thumb drive and use Unetbootin to create the bootable usb.
[[COLOR="RoyalBlue"]http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

---


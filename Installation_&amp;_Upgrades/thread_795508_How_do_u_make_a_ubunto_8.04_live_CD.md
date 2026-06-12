---
title: "How do u make a ubunto 8.04 live CD?"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Pno3 on 2008-05-15
I have downloaded the Ubuntu 8.04 ISO and have wasted 10 CD's in the process of trying to make a Ubuntu 8.04 bootable CD. How do you do it?

---

### Post by amingv on 2008-05-15
How are you burning it? You're not burning the ISO file to a cd, are you?
Generally just open the ISO file with your burning software (most of the time a double-click will do) select the minimum possible burning speed and burn.

---

### Post by Afkpuz on 2008-05-15
You need to actually write the image to the disc, not just copy the iso to the disc.  Go here and download this program

[http://www.download.com/3001-2646_4-10792184.html?spi=aabf3684c2c6d3a78c15f419d41cbd7c](http://www.download.com/3001-2646_4-10792184.html?spi=aabf3684c2c6d3a78c15f419d41cbd7c)

If that doesn't work at a low speed, I'd say your drive is busted.

---

### Post by Achetar on 2008-05-15
First, I would recommend getting a CD-RW disc to use, then you dont have to keep burning new ones. My question is are you using Windows, Mac OS X, or Linux? I am assuming Windows.

You need to download [this]("http://isorecorder.alexfeinman.com/isorecorder.htm") ([direct link for XP SP2]("http://isorecorder.alexfeinman.com/download/ISORecorderV2RC1.msi")) to burn ISO images to a cd, or use Roxio easy CD creator or another program that can burn CD images. (I like the one I recommended because it is free and works great).

Then put a blank CD-R or CD-RW disc in the drive and use you CD-Burning program to burn the Image to the Disc. When you reboot, enter your BIOS using whatever key it says (most common is F2) Check and make sure that the Boot Order has CD-ROM (or DVD-ROM) is about Hard Disk. Then Save any changes you made and reboot one last time with the Ubuntu CD you burned in the drive. It should show the ubuntu logo and several options. Select the top one and the LiveCD will boot.

Hope this helps!

---

### Post by Pno3 on 2008-05-15
(I am running XP) What I am currently doing to opening sonic (DC righting program) adding the ISO (without changing it, so it is exactly the same as when I downloaded it from the Ubuntu home page)and start the burn. After I finish the burn, I just pop it in the CD tray, and then restart, sometimes i get the option to install Ubuntu, but it dose not let me run Ubuntu from the disk without installing. I tried looking up how to make an Ubuntu live CD on google, and found this page 

[http://www.stchman.com/create_cd.html](http://www.stchman.com/create_cd.html) 

But I have not clue what it is talking about and I have never even heard of doing it that way.

---

### Post by joegiampaoli on 2008-05-15
Sounds like an error on the cd or when you downloaded the cd image. Try doing a disk check on the menu when you boot the computer with the ubuntu CD. When you burn a linux iso it's best to not go above 8X speed, the slower the better. make that "Test CD for defects" test and see if it spits any errors, it should take about 3 minutes.

---


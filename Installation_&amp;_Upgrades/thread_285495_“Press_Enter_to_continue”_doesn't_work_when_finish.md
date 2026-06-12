---
title: "“Press Enter to continue” doesn't work when finishing installation"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by aochoa on 2006-10-26
I just finished installing Ubuntu 6.10 in a new computer that I just got specially to start using Linux and stop using Windows. I even formated my hard drive without even given a chance to Windows Media Center (I hope it wasn't a mistake), and before I reboot to check if it is going to work I want to ask if someone knows why the next thing happened on this computer:

At the end of the installation when I get the message:
"Please remove the disc, close the try (if any)
and press Enter to continue", nothing happens. The same thing happened with Ubuntu 6.06 and Kubuntu 6.10. 

I also would like to ask if you know where can I find the proper drivers for some of the devices on my computer, because I have read so many bad experiences with ATI that I just realize that I may have got the wrong computer for Linux (I promise that I will help others as I start getting better with it)

The main computer's specifications are:

- DELL Dimension 9200

- Intel Core 2 Duo E6400

- Graphic Card 256MB ATI Raedon X1300 PRO ](*,)

- Audio Software Integrated Sound Blaster Audigy Advanced HD

- TV Tuner Integrated Analogue PCI

Any advice would be appreciated

---

### Post by deepwave on 2006-10-26
Just try to restart the computer without the disc, and you should be fine.  This should work even if you have do a hard reboot (holding the power button).  **Try not to do a hard reboot if you can avoid it.**

As for the ATI drivers, don't worry too much about them just yet.  Ubuntu should work with non-accelerated graphics out of the box.  So you will not get your 3d graphics at first boot.  But changing that is pretty easy.

Hope that helps.

---

### Post by aochoa on 2006-10-26
Ubuntu is working now.
The graphics are not great. Screen resolution at 1024x768, 61 HZ
It's 4:07 am. Time to go and count sheep. Tomorrow when I am more "awake" I will look at how to install the ATI Driver for my **Graphic Card 256MB ATI Raedon X1300 PRO**. It's so annoying no to be able to get the optimal results because some companies are so greed. *Is any one from AMD-ATI listening?*. I have known that  in advance I would had never bought a computer with an ATI card.

---

### Post by DonKyot on 2006-10-28
Hi aochoa, I'm just trying to install Ubuntu on a 9200.
The installation doesn't find the network card on mine.
Did you not have this problem? If not, which installation are you using?

cheers

---

### Post by deepwave on 2006-10-31
@DonKyot: Can you specify what network card you have?

lspci | grep Ethernet

---

### Post by DonKyot on 2006-11-01
> **deepwave said:**
> @DonKyot: Can you specify what network card you have?

lspci | grep Ethernet
Hi,
it's the G965 (see [thread]("http://ubuntuforums.org/showthread.php?t=286015"))
Joke is, even the windows dist. doesn't support it!
> 00:19.0 Ethernet controller: Intel Corporation Ethernet Controller (rev 02)


Actually. I have now managed to get 97% of the full Edgy installation on the box.
The only thing that isn't working now is the bluetooth - something in the boot script stuffs the wireless keyboard & mouse.

---

### Post by aochoa on 2006-11-02
> **DonKyot said:**
> Hi aochoa, I'm just trying to install Ubuntu on a 9200.
The installation doesn't find the network card on mine.
Did you not have this problem? If not, which installation are you using?

cheers

DonKyot: I installed Ubuntu 6.10 64bit. Everything worked well except SKYPE. I couldn't configure the sound and it kept crashing. It's very annoying because there is not a 64 version of skype and all the work arounds always messed with something else.

Before I tried Ubuntu 6.10 i installed Kubuntu 6.10-rc and it installed without problems. I can't remember why I did uninstall it :-k 

Debian GNU/Linux 3.1 r3 "Sarge" couldn't mount the DC-ROM. 

Debian GNU/Linux testing "Etch" couldn't mount the CD-ROM. 

The daily built image from Debian (02-November-2006) mounted CD-ROMs properly but didn't find the network card. 

SuseLinux Desktop 10 didn't recognize the Network card nor the Graphics Card

... Trying 6.10 32 bits right now ..

If you find any more information please let me know.

---

### Post by DonKyot on 2006-11-02
Hi.
I'm now working with the full 6.10 release... just boot using 'generic'
I had problems with the desk top distribution disk originally; after a while I tracked that down to something clobbering my bluetooth keyboard and mouse - with hindsight, not a wise choice!
Network, both CPUs working, etc. Only remaining niggle is not having the most up to date ATI driver in the kernel (I get 1680x1050); but I can live without acceleration for now.

---

### Post by lovepolo on 2006-11-02
Hello,

I finally got time to install 6.10 into my new 9200 last night, but failed. My configuration is kinda weird, I have the original SATA harddrive and dvd, I installed a PCI ATA raid card, then 2 ATA harddrives as raid-0,  and 1 ATA DVDRW. Right now Windows is running on raid-0 ATA harddrive, I am trying to install 6.10 on SATA drive. 

I tried 64bit Alternate and Server, both  cannot boot, it is weird when installing it did not ask me where to install grub, and the system insalled grub on the raid-0 ATA drive, definitely not I want.

Anyway, DonKyot,

Can you share more details of your installation, which iso image you use, did you change the setting in BIOS from RAID on to AUTO? I am also instereted in how you partition your drive.

---

### Post by DonKyot on 2006-11-03
> **lovepolo said:**
> 
Anyway, DonKyot,

Can you share more details of your installation, which iso image you use, did you change the setting in BIOS from RAID on to AUTO? I am also instereted in how you partition your drive.

Hi,
yes I also started with RAID0 and I don't believe that was a wise move. Most comments about that I found suggested
a/ it wasn't worth it for speed unless you're using really really big files (video, db etc.) and
b/ getting grub to work with RAID-0 is really really hard.

So, yes. I ditched RAID. This means loosing the Windows installation - if you have one. Re-installing windows was slightly problematic; the Dell dist disk doesn't have several drivers on it, including... yes you guessed it... the network drivers!! So, if you do that. down load the network drivers from dell onto a USB card or something before you start.

Having done that, you should be able to install the desktop ISO.
as mentioned, I've a wireless k/b & mouse - and have had to set HIDD_ENABLED=1 in /etc/options/bluetooth (after booting in rescue mode).
I don't have the up to date ATI drivers installed - to much hassle - so not optimal.

hope that helps.

---

### Post by lovepolo on 2006-11-03
Thank you, will try it again hopefully this weekend.

---

### Post by aochoa on 2006-11-04
> **lovepolo said:**
> 
Can you share more details of your installation, which iso image you use, did you change the setting in BIOS from RAID on to AUTO? I am also instereted in how you partition your drive.

Everything seems to be working fine on my DELL DIMENSION 9200 now with Ubuntu 6.10 i386 "Edgy Eft".
 
For your information I left the BIOS with the original configuration.

Make sure that you download Ubuntu or Kubunut's latest version. By mistake I downloaded the previous version because I scrolled very quickly looking for the "mirrors" in UK and I didn't notice that the "mirrors" at the end of the page were for version 6.06 and I did it the same thing for 32 and 64bits. ](*,) And when you install there is not a single advice of which version you are installing. You know, you are tired and want to do things as fast as possible and after being trying version 6.06 in the past I assumed that everything on the download page now was for version 6.10.

Anyway, let us know if you succeeded on your installation

---

### Post by lovepolo on 2006-11-10
Hello all,

Now I successfully installed 6.10 into my dimension 9200. 

If you read my previous post, I have a PATA RAID in my machine. This time, when I installed Ubuntu, I unplugged those PATA drives, and install Ubuntu to SATA drive comes with Dimension 9200. Then after the installation, I put PATA RAID back in, installed dmraid package, modified grub, everything is ok.

---


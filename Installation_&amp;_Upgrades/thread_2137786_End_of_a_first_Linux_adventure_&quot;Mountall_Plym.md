---
title: "End of a first Linux adventure &quot;Mountall: Plymouth command failed'"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by Mister Max on 2013-04-22
Dear all, 
I need some help and I wann stress, I am a total Linux/Ubuntu Newbie.

Installed Ubuntu yesterday, My ISO image is a bit older (Ubunt 10.4), but the installation was done with web connection, I believe therefore, the actual installation is more up to date... I cant check though, since Ubuntu does not boot.

A clean installation, no parallel Win OS or anything, was successful.

The frist boot after installing however produces a halt at:
"Mountall: Plymouth command failed" (in German: "Plymouth-Befehl fehlgeschlagen")
"Mountall: No connection to plymouth'' (in German: "Keine Verbindung zu Plymouth")

The Forum is still a bit of a jungle to me. Too many shortwords which I dont understand. Nonetheless, I believe this problem might not occur the first time.
I believe I understood, that Plymouth is responsible for the start up screen and other things.
Also I read somewhere, that Nvidia Graphic Controllers tend to create trouble with Plymouth.

My computer is HP Pavillon DV5 with Nvidia Graphic Controller.

Any hints on what I could do?

Thank you so much!

---

### Post by mlentink on 2013-04-22
You seem to have a working internet connection. Download a current version of ubuntu, burn it to cd/dvd or a usb stick (you can use the live version on the cd that you have) and install that. Your nVidia card will be supported with the OS drivers. or you can later install the proprietary drivers if you need to.

---

### Post by coldraven on 2013-04-22
As mlentink says, get a newer version. 12.04 LTS or if you want cutting edge get 13.04 when it is released in a few days.
I usually download the using a torrent, it is fast! 
You can see all download options here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

I usually install from a memory stick or SD card, it it faster and does not waste a CD.
You can create one using Unetbootin, it runs on Windows, Mac and Linux.
Get it here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

To boot from a stick or card you need to open the BIOS (setup) screen at boot time and change the boot order to make USB the first option.
You have to press F2 or F10 or some other key depending on your model to get to the the setup screen at boot time.
After a successful install change the boot order back to booting from the hard drive first.

Good luck!

---

### Post by Mister Max on 2013-04-22
Thanks Gentlemen (? and Ladies?)!

Alright, Ill do that. I already feel clever now having used a USB Stick during my first installation... :)
From your recommendations I conclude, that Ubuntu installation updates do not exceed the leading version number?
A 10.xxx will remain always a 10.xxx?

Good to know!

Thanks!

---

### Post by mastablasta on 2013-04-22
> **Mister Max said:**
> From your recommendations I conclude, that Ubuntu installation updates do not exceed the leading version number?
A 10.xxx will remain always a 10.xxx?


you would be prompted for upgrade to 12.04 (which is the next LTS version). now the upgrade takes abotu 2 hours while a fresh install that includes formatting would take you less than 30 mins. since you dont' have any data on mashicne it might be easier and faster to do a fresh install.

note that there was a huge change in default interface in 12.04 (as compared to 10.04). if you want something like previous interface then you need to search for gnome classic/fallback or use Xubuntu (uses Xfce interface(. if you want something that kind of looks like windows then you are after Kubuntu (uses KDE interface) or for example Cinnamon interface.

back to your original issue - drivers in linux are often included in kernel so 12.04 which is from year 2012 (12) month April (04) will have a newer kernel and as such also newer drivers. so it might work better with your PC out of the box. 
but then again you might get the same issue as before. if you can 't progress past the boot screen you can try one of the boot options. particulary *nomodeset* option might let you pass. here is some info on them: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

10.04 will reach end of life within a month or so. it had 3 years of support. new lTS (12.04) will have 5 years of support. if you want to use can also use releases that are between LTS but they only have 9 months support and new one comes out each 6 months (in April and in October). next LTS is 14.04 - So in April next year.

---

### Post by Mister Max on 2013-04-22
Okay everyone, huge progress! 
Thanks very much! I am writing from an Ubuntu OS

Ubuntu 12.04 is running stable and booting without complaints. Graphic seemed okay (no videos or anything tried yet.
Compared to the earlier installation routine's of-disk OS though, the  Wifi Drivers dont seem to work. 
I installed Jockey to find additional drivers (not part of 12.0x apparently).

From What the OS says now under System Settings > Software sources > Additional Drivers:

In regard to graphic controller Nvidia Geforce 9600M GT:
It at the moment seems to be run by "X.Org X server - Noveau Display Driver from xserver-xorg-video-nouveau (open source)"
"The Device is using an alternative driver"
I am not sure if installing the jockey pack did anything there... 
According to this guy here one should be careful when trying to switch to the Nvidia binary drivers 
[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)
He promises black boot screens. As I the grapgic interface seems a little slow... Hmm. 
Ill try it out... lets see what happens :)

Next Baustelle (german for construction site):
Broadcom Corporation BCM 4312 802.11 b/g LP-PHY:
Using broadcom 802.11 Linux STA wireless driver from bcmwl-kernel-source (proprietary)
I am using a LAN Cable, the Wifi does not work at the moment. The configuration seems very different from Windows. is there really no scanning for which networks are available? I might just be too dumb.
As said, it did when during installing the 11.04 version..
Any ideas here?

As I want to try keep things a little I will try to clarify the many other remaining questions in the forum. (Skype, Dropbox and so on)

Thanks so much!

---

### Post by matt_symes on 2013-04-23
Hi

Jockey was removed from 12.04 for a reason. 

It kept crashing people computers when installing graphics drivers. 

Don't use it !!

Search for "additional drivers" in the dash and use that instead.

Kind regards

---

### Post by Mister Max on 2013-04-23
Noted...
Aright! I will try sort out the rest of the issues in separate forums to allow other people to benefit! 
Thanks everyone! ou kept me in the boat!

---


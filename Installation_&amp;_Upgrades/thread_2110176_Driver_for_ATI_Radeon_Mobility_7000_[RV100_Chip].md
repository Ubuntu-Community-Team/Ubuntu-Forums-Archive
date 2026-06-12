---
title: "Driver for ATI Radeon Mobility 7000 [RV100 Chip]"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by 122jdh on 2013-01-29
Currently I have Lubuntu 12.10 on an iBook G3 Dual-USB w/PPC architecture. It works for minor things like typing this paragraph, but other than that its crap. I have so many problems with it: Unsupported Video Card (ATI Radeon Mobility 7000 [RV100 Chip], Unable to display the programs needed to fix that, can't update drivers for my audio card, etc. What version of Ubuntu, LUbuntu, Mint, Fedora, etc supports this video card right from the begining? Audio wouldn't hurt either. (It needs to be a Power PC compatible OS)

---

### Post by SpiderSkull on 2013-01-29
None of them would support your video card right from the install. You need to find a driver for it. search google for fglrx that's AMD/ATI drivers for ubuntu.

Wich version of Ubuntu 12.10 did you download?
because there is an version for power pc.

Other OS sugestion: Debian

---

### Post by snowpine on 2013-01-29
Your hardware is a decade old. Here are some systems that are known to run Ubuntu (and its variants, like Lubuntu) flawlessly:

[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by 122jdh on 2013-01-29
I have searched endlessly and cant find that driver

---

### Post by Grinage on 2013-01-29
I don't know that any distro will support your video card out of the box, but with any of the ~buntu versions there are plenty of options.  If you have internet access and the live CD correctly detects and uses your LAN or WLAN card, after install and updates video issues typically resolve themselves.   Sometimes, however, there are some machines that are 'special'.  Getting sound and video functioning on these 'special' machines can be a challenge. 

As for updating, try updating from terminal, using the following commands
sudo apt-get update
sudo apt-get upgrade

if that runs and picks up correct audio and video drivers and settings you're good, if not post back with output from lshw

---

### Post by 122jdh on 2013-01-29
Ran those commands and updated everything that was out-of-date. Turns out I already had audio drivers. So only my video driver needs updated.  I should have said what release version when I started this thread.

---

### Post by mörgæs on 2013-01-29
> **122jdh said:**
> So only my video driver needs update. 

Why? Doesn't the open-source driver work well?

---

### Post by Grinage on 2013-01-29
[http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html)

video driver for radeon, this is for I386 if you can get into a package manager like synaptic you can search for radeon in the packages for your system.

---

### Post by 122jdh on 2013-01-29
I went to that site and got the File for PPC and installed it. Didn't work

---

### Post by Mark Phelps on 2013-01-30
Sorry, but that video card came out in 2001 -- 12 years ago!  AMD dropped Linux driver support for that card years ago.

If you are seeing a desktop, then you are running a generic Radeon driver -- and that is the best you're going to get today.

---

### Post by mörgæs on 2013-01-31
A lot of misunderstandings in the thread. Just to sum up:

There are open- and (sometimes) closed-source drivers for an ATI/AMD video card. Open-source drivers (called Radeon) are the ones mentioned in 
[http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html)
Don't invest long time in reading - it's hardly relevant to the ordinary user.

They are part of the kernel by default, so no need to install anything. Once a driver is in the kernel it is unlikely to be removed, so expect support for many years. The fact that you have a screen picture now shows that they are working. 

Closed-source drivers (called fglrx) are released only when ATI/AMD pleases to do so. According to them a video card has a short life time, so drivers will only be provided for a few years - planned obsolescence. For this card support ended long time ago.


More here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Grinage on 2013-01-31
there are some radeon packages in the repositories but I don't know if they'll help you if the card is very old.  In your favorite package manager try searching for radeon just the word radeon and see what comes up, if you use Ubuntu Software Manager you may have to ask it to show technical or hidden items to find it.

---


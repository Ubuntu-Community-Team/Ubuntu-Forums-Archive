---
title: "Narrowing down the Distro's to Install Ubuntu"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by tamarku on 2005-08-31
Current System Configuration: 
AMD Sempron 2400+ processor
768 mb RAM
HD0 40 Gig
HD1 80 Gig
NVidia Geforce 5200 video card. 

OS's: 

40 Gig:
Windows XP Home HDA 0
Linspire HDA 1

80Gig:
HDB3 Linux SWAP
HDB5 is a fat32 storage partition with pictures, movies and MANY MP3's
HDB6 PCLinuxOS

Right now my system boots using the Linspire GRUB loader.  I would like to get rid of having 2 distros.  I do need to keep Windows XP for work purposes.  I would like to delete the Linspire and replace this partition with Hoary  5.04.  I would like to delete the HDB6 altogether and regain that space for more pictures and such.  

How do I delete Linspire, PCLinuxOS and install Ubuntu in HDA1 partition?  I have been using the LiveCD for about a week now and I love it.  Ubuntu has been my favorite.  What made me try it was that it was a Gnome desktop, I have tried all KDE desktops so far, this is nice but the Gnome appeals to me more.  Plus, I read somewhere that if you really want do I could apt-get KDE for Ubuntu and log out of Gnome and Load KDE, is this true?  Also, If I delete Linspire and PCLOS do I need to do a WinXP Fix MBR?  Or will that not be necessary since I'll be installing Ubuntu and just tell Ubuntu to load Grub into the MBR.  I feel *pretty* comfortable with this but guess before I start I few ideas would be great.  This is my first post to Ubuntu and I still consider myself a Newbie.  Any and All help will be greatly appreciated.

---

### Post by Lord Illidan on 2005-08-31
You can do it pretty easily from the Installation CD... and no, Windows won't be touched.. trust me, I've installed and re-installed tons of distros and I haven't had any problems..

How I would go about it is using the partitioner in the Installation CD..

Format the linspire partition and set it as /

Make sure the Swap partition is still set as swap..

And format the PC Linux OS partition to ext3..

And yes, if you get bored of Gnome, you can install KDE...
Just do this ```
sudo apt-get install kubuntu-desktop
```

EDIT : Grub will probably present you with an option to put MBR on primary hard drive or partition.. select yes..

---

### Post by tamarku on 2005-08-31
You said: 

"And yes, if you get bored of Gnome, you can install KDE...Just do this
Code:

sudo apt-get install kubuntu-desktop"

Does this then mean that I can still switch between Gnome and KDE still? AND, how does someone go about switching their UI?  

Thanks for the quick response.

---


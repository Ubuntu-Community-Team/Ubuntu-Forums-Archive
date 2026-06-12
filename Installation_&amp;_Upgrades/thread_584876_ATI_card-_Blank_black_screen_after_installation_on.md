---
title: "ATI card- Blank black screen after installation onto empty hard drive"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by landcross on 2007-10-21
ATI card- Blank black screen after installation onto empty hard drive

I have installed this now 4 times each time reformatting the drive.

Installed  7.1 Ububtu from Live CD, which works fine on the Live CD.

Every occasion the same……it installs the files correctly on the hard drive, but I just cannot start X.  I know the problem is my ATI card.

I had no problems with the beta release.

Giving up on this version of Ubuntu until someone provides a fix for ATI cards


Intel Core 2 Duo
Memory 2 GB
ATI Radeon X1650SE
32 inch LCD

---

### Post by linuxaz on 2007-10-21
Hello,
It would appear the many people are having this same problem.  it is listed in Launchpad, and all over Google concerning the Gutsy release.  I see that some people had luck getting the ATI driver to work by disabling "dri" in the /etx/X11/xorg.conf file.  Also, depending upon the graphics card you have, 3d may be possible using open source drivers....... if so, Ubuntu should pick that up upon installation.

I managed to get mine to work on my ATI 220m xpress card on my laptop.  While fglrx installed in both suse 10.3 and Gutsy, compiz seems to only work on Ubuntu :(

linuxaz

---

### Post by drama1981 on 2007-10-21
its very possible its setting your card as generic (vesa). for some reason its doing that on about half of the ati cards out there. do 

sudo dpkg-reconfigure xserver-xorg

when prompted for driver select ati. go through the rest of the configuration. after that is done.

do

sudo /etc/init.d/gdm restart

---

### Post by beerfan on 2007-10-21
> **landcross said:**
> ATI card- Blank black screen after installation onto empty hard drive

I have installed this now 4 times each time reformatting the drive.

Installed  7.1 Ububtu from Live CD, which works fine on the Live CD.

Every occasion the same……it installs the files correctly on the hard drive, but I just cannot start X.  I know the problem is my ATI card.

I had no problems with the beta release.

Giving up on this version of Ubuntu until someone provides a fix for ATI cards


Intel Core 2 Duo
Memory 2 GB
ATI Radeon X1650SE
32 inch LCD

My friend has a X1650 Pro and he has this same experience with either Feisty or Gutsy. I tried to help him install various ATI drivers in Feisty but I couldn't get it working.  If you get this figured out please share what you did.

---

### Post by bruceee on 2007-10-21
Hi all, I had the same black screen problem while trying to run the gutsy live cd, finished up defaulting motherboard bios and noticed "init display " went from AGP to PCI, was then able to Ctrl-Alt-F6 when the screen went black and then Ctrl-Alt-F7 to turn X back on and after that all worked. Installed and updated to restricted driver and lo no probs at all now.
Regards   Bruceee

Athlon 64 on GA-K8NS
ATI Radeon 9800xt  AGP

---

### Post by micahdorn on 2007-10-21
I'm having a problem that seems related. ati card installed, and my screen put up an error message that the picture was out of range, please et screen to default res and refresh rate. but then i restarted and got the same message, but i just left it for a bit and it eventually loaded fine. just restarted my computer for the first time and now it wont load again. it just goes black and cant even get to a  terminal with ctrl alt f*

any suggstions?

ps.   i can load into the live cd now. ( i couldnt before.)

---

### Post by crag277 on 2007-10-25
Yes, I am having the same problem with my Sapphire Radeon X1650 AGP, 512MB.  The problem, for me anyway, is not just Ubuntu, it's linux as a whole.  I have tried Ubuntu Edgy, Feisty, Gusty, PCLinuxOS 2007, Mepis 6.5, Mandriva 2008.0, and maybe another couple ditros.  Point being, on each of them as soon as the fglrx driver is installed I get a black screen and no response every time when trying to boot.  Very frustrating.  Looks like the old 9700 Pro may be seeing some more use after all...

---

### Post by mnewell on 2007-10-25
After much fooling around it appears the option "AGPFastWrite" causes my system to lock up when set to "true" (which it is in my original configuration file).  I commented it out and now I don't get lockups, but I still can't get the display to run on the external monitor.  Grrrr!

---


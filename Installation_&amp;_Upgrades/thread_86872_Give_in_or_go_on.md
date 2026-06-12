---
title: "Give in or go on?"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by nilsA on 2005-11-06
I have an old BE6-based Pentium III, 500 mhz computer/S3 graphics. It runs WIN2000 without problems; is shaky with WIN98; KNOPPIX from CD - no problem, an old Caldera OpenLinux desktop installs most times without a problem. Other distributions, just problems.

Ubuntu seems the most promisisng. I can get to the command line, but no graphical interface installs.

I'm one of those who (a) realizes that Linux may make my old computer a good "workhorse" for Internet and word processing - what is mostly what I do.

So, is it possible to go on from the command line, to install the rest? The computer obviously connects to the Internet to download stuff for language support (Norwegian, not on the CD); resets and starts installing the graphical interface, then jumps into line mode.

One thing making me really fell like giving up is this: The fault messages seems to vary from one installation attempt to the next.

---

### Post by aysiu on 2005-11-06
Well, it sounds as if you might have done a server install. If you do the regular installation, there *should* be a graphical interface. If you're at the terminal already and want to try it, type this in (after you log in): ```
sudo apt-get install ubuntu-desktop
``` If Knoppix worked, though, you can also install Knoppix to your hard drive (it's famous for being a live CD, but it installs, too): [http://www.knoppix.net/wiki/Knoppix_Installer](http://www.knoppix.net/wiki/Knoppix_Installer)

---

### Post by az on 2005-11-06
[QUOTE=nilsA]I 
Ubuntu seems the most promisisng. I can get to the command line, but no graphical interface installs.
[/QUOTE]

Some old S3 video cards are improperly configured to use too high a color depth.  Can you boot into recovery mode?  If so, type
dpkg-reconfigure xserver-xorg 
and answer the questions.  Towards the end, you will be asked about color depth.  Pick 15-bit ans see if that helps.

Run
init 2 
to go from recovery mode to desktop mode.

If you are worried about the install not happening properly, run
sudo apt-get -f install 
to see if everything is installed okay.

---

### Post by nilsA on 2005-11-07
Seems I can't get X loaded properly. The advice of both of you works - to some extent, but in the end the first - installing ubuntu-desktop - ends in a neverending rolling screen; so fast I cannot read what's there.

I have located a newer S3-card, and will tomorrow attempt to reinstall with that card. I have also downloaded a new iso. The first one obviously does not work; the second is maybe giving some problem. In general, both seems to have problems the "debootstrap" program - whatever that is. In the end, if I repeat, it will eventually correct.

---


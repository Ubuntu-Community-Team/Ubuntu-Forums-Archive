---
title: "Xubuntu 8.04.1 Instal Freeze"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by jr4902 on 2008-08-20
I have been trying to install Xubuntu 8 since early May but so far have not succeeded.  However I have been able to install Xubuntu 6 LTS.  The live CD works flawlessly for Xubuntu 6.06, 7.1 and 8.04, at least until I try to do an actual installation.

I have checked the CD integrity and ISO chksum.  I have tried the Live and Alt CDs, burning them at 4x speed.  After reading other "install freeze" posts I have tried the options suggested when hitting F6 at the install screen.  I have also tried Wubi.

The Live CD instal freezes at 81%, "configuring target system".  I have tried this at least 6 times, leaving the computer overnight, just to make sure it is frozen, not just taking time to install something.  It freezes at the same freeze point for the Live Cd and Wubi.

The Alt Cd freezes at 68%, "selecting and installing Software - configuring gnome-keyring".  I have tried this at least 4 times, leaving it overnight after the first freeze.

My latest attempt is to use the Alt Cd and at the install screen, hit F4 and select "install a command line system".  (I also tried the "normal", OEM and LTPS Server modes; all froze at configuring the gnome keyring).  The command line system installation worked.  I then typed the following lines which I found on another thread:  sudo nano /etc/apt/sources.list (uncommented internet addresses); sudo aptitude update; sudo aptitude install xubuntu-desktop.

The computer froze during the installation of the Xubuntu desktop at "setting up capplets-data (1:2.22.1-Oubuntu4.1)".

I am still new to Ubuntu, and appreciate any and all suggestions.

My system info:  5 year old computer, EliteGroup motherboard, AMD 3100+ CPU, 480 MB RAM, integrated video and audio, Xubuntu 6.06 installed on primary 40 Gb drive; had moved Windows XP to 10 GB slave drive, but am now attempting to install Xubuntu 8 onto slave drive.

---

### Post by jr4902 on 2008-08-29
This is not a solution, but it is a step that worked for me.

I spent all day Monday attempting to break through the freeze at installing the Xubuntu desktop.  After many resets, I made some progress, but had a growing list of dependency issues, mostly stemming from dbus not configuring properly.

So I tried something new.  I downloaded OpenSuse 11(KDE), burnt the ISO to CD and installed it.  There was not so much as a hiccup!!  It installed flawlessly.

I can't say that I am happy to leave Ubuntu/Xubuntu.  I like the concept of different flavours for different systems rather than just KDE or Gnome, but my only choice with Ubuntu was Xubuntu 6.06 which will no longer be supported after April 2009.  

After reading many threads, I know that I am not the only one with freeze/lock-up problems.

Could 6.06 be supported (after April 2009) until a solution to the freeze/lock-up problems is discovered?

---

### Post by jr4902 on 2008-09-17
One week ago I tried another step.  Since OpenSuse installed so easily, I tried Kubuntu 8.04.1 using the alt CD.  It wasn't quite as easy as OpenSuse.  The installation froze at configuring gnome key-ring and again at libgnome-2.  Instead of making several attempts to complete the installation, I installed a command-line system, then installed the Kubuntu-desktop.  

From all of this, it seems that the freeze-ups on my system are related to gnome.  For whatever reason, KDE has no problems.  And I am happy to be able to stay in the Ubuntu community.

---


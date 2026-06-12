---
title: "Display errors."
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by danhenry on 2007-05-11
Hey everyone. I just recently installed the Ubuntu Feisty Faun server edition onto a spare computer of mine. I then went through and upgraded it (using: "sudo apt-get install-desktop") to get gnome into it. The problem is, now that I've done that, whenever I boot the computer, I hear the sound it makes when it gets to the login screen, I just see a blank black screen. I can even type in my username and password and then the sounds play to sign into the OS. Any suggestions? I'm guessing a driver issue, but I'm pretty sure this computer has a built in video card to the motherboard. Thanks!

edit: I got into BIOS and it says the active video is "Intel 815 Chipset Video BI"... doesn't mean much to me, as I've never heard of that before. Might help a little though.

---

### Post by fakie_flip on 2007-05-11
You might need 915resolution.

$ apt-cache search resolution intel
915resolution - resolution modification tool for Intel graphic chipset
request-tracker3.4 - Extensible trouble-ticket tracking system
request-tracker3.6 - Extensible trouble-ticket tracking system
chris@ubuntu:~$ apt-cache show 915resolution 
Package: 915resolution
Priority: extra
Section: universe/x11
Installed-Size: 124
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Steffen Joeris <white@debian.org>
Architecture: i386
Version: 0.5.2-10ubuntu1
Replaces: 855resolution
Provides: 855resolution
Depends: libc6 (>= 2.5-0ubuntu1), vbetool (>= 0.6.1)
Conflicts: 855resolution
Filename: pool/universe/9/915resolution/915resolution_0.5.2-10ubuntu1_i386.deb
Size: 14362
MD5sum: c0382ca85547546e9670efb1d9e30bde
SHA1: 84c1cb2c519b99206b266fdb7f5eda51c5305064
SHA256: 915e88da451f41232239ffccc648030a2d4282d439085faa21eb236fc5e0a7ff
Description: resolution modification tool for Intel graphic chipset
 915resolution is a tool to modify the video BIOS of the 800
 and 900 series Intel graphics chipsets. This includes the 845G,
 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
 This modification is necessary to allow the display of certain
 graphics resolutions for an Xorg or XFree86 graphics server.
 .
 915resolution's modifications of the BIOS are transient.
 There is no risk of permanent modification of the BIOS.
 This also means that 915resolution must be run every time the
 computer boots in order for its changes to take effect.
 If you want to automatically set the resolution on each boot
 and before X is launched, see /usr/share/doc/915resolution/README.Debian
 for information about configuring the provided initscript.
 .
  Homepage: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by danhenry on 2007-05-11
Hmm. How would I go about getting that to load whenever I boot? Instead of manually loading it every time?

edit: And how do I boot into the gnome from the server terminal? What command is that? (Sorry, I'm quite new to Linux)

---

### Post by fakie_flip on 2007-05-14
sudo crontab -e

Add this line to the bottom

@reboot command

Save and exit.

Replace command with the command that you want to run on boot.

---


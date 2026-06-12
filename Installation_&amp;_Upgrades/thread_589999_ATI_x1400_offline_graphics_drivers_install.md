---
title: "ATI x1400 offline graphics drivers install"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tnunamak on 2007-10-24
Hi,

I'm using a dell inspiron 6400 with an ati x1400 graphics card, and I can only run ubuntu from the command line. I've tried changing xorg.conf to use ati and vesa drivers, but neither works. I cannot download any packages from the command line because my university uses cisco clean access, and I cannot connect to the network/internet without logging in to clean access via a web browser (ugh).

As far as I know there is no linux client for clean access, so the best I can do is to download all of the graphics drivers into a shared FAT32 partition that I can mount from ubuntu and install them from my hard drive. To do this, which drivers would I need, and how can I install them so that I take care of all the dependencies? Thanks.

---

### Post by crisponions on 2007-10-24
you could try to download these packages:
linux-restricted-modules-generic 
restricted-manager
xorg-driver-fglrx

Then run
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

or
check out Method 2 of this link [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---


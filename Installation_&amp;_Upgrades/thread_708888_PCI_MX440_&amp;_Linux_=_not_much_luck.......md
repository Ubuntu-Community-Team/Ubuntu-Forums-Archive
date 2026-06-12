---
title: "PCI MX440 &amp; Linux = not much luck......"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by jabeez on 2008-02-26
Hey all, I'm trying to put together an old PC for a friend, currently a Celeron 1.3 Ghz with 512mb RAM and a newly acquired MX440 PCI graphics card, which I thought would make my life much easier. Unfortunately, very few distros (live CD's) I try will boot up to a working Xorg. None of the 'Buntus or their derivatives will work, the only ones that will is PartedMagic 2.0 and Mepis (and AnTix (Mepis)). It seems as though they all try to use the onboard Intel graphics (horrible), and I've tried many boot parameters (safe mode, etc.) to no avail. Bummer, was really hoping to try out and XFCE distro like Xubuntu or Mint XFCE, but neither will even get to a working desktop, which means no install. Any suggestions??? 


ps.: Onboard graphics are supposedly disabled in the BIOS, but apparently these Live CD's are still trying to configure that instead of the PCI.......

---

### Post by Sam Lars on 2008-02-26
You should be able to go into xorg and reconfigure it to use that PCI device instead of the Intel, provided you have the drivers for it.
```
sudo dpkg-reconfigure xserver-xorg
```
Look in the /var/log/Xorg.0.log.  A bit of the way down it does a PCI scan, and will list all the devices it finds.  You can get the PCI address there (something like 0:10:0).  In the above command, there will be a place to enter that eventually to tell it to use that card.

---

### Post by jabeez on 2008-02-27
yeah but that's the kicker, all the distros I wanna try out are on live CD's, but very few (actually none of the 7-series 'Buntus (or their derivatives) I've tried) will even boot, leaving an install impossible. That's what's so frustrating, as cool as live Cd's are, if you have any problems you're kinda SOL...........

---

### Post by Sam Lars on 2008-02-27
You can still edit the X configuration file and restart it on the live CD.
There's always the alternate install disc that will install in text mode without the GUI.

---


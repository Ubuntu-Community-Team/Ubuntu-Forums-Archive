---
title: "/boot partition filling up quickly need to delete old kernels"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-07-06
how would i go about deleting my old kernel?  i have my ubuntu machine partitioned the way gentoo would partition a drive with a seperate boot directory.  my boot directory is only 200 megs so i can probably fit 4 kernels max into it and need to eject the old ones.

---

### Post by ajgreeny on 2011-07-06
I suggest next time you install, you get rid of a separate /boot partition, as it complicates things for most situations.

However, for now, you can remove old kernels most easily by using synaptic, search for the kernel number, eg 2.6.32-31, 2.6.32-29 etc etc, and remove all the packages with those exact old numbers, usually a linux-image and two linux-headers packages.  It's best to keep the most recent and the one before that, just in case.

---

### Post by drs305 on 2011-07-06
Here are some other ways to remove them, including via the GUI app Ubuntu Tweak:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by boblizar on 2011-07-08
not as urgent as you were expecting.  simple maintenance question....  if i was REALLY in a pinch for space i would of rm -rf /boot/imagetoberemoved because i operate that way and am strugling with debian package management and can not get a source debed for the life of me

---

### Post by crtlbreak on 2012-06-13
as a rule (and good nix practice) it is unadvisable to "rm -rf"  anything  - a little like shooting pigeons with buckshot :p.
code
sudo rm /boot*2.6.32.nn*

where <2.6.32.nn> is the kernel number  - [starting with the lowest number first]

will remove the specific number related kernels in group format (config, vmlinuz etc) - typically linux - many ways to skin the cat.

---


---
title: "can i run ubuntu live, then install to hdd from a flash drive"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by phantommaggot on 2007-03-14
Just as the title says. 

im have this goal of getting linux, beryl, and touchscreen all working on a fujitsu p1510d

i know i can either buy an external bootable usb dvd rom, or install from a flash drive.. if thats possible.. 

i know that linux can be installed TO a flash drive, but thats not exatly what i want to do...

i want to be able to run the live OS off of a flash drive, or be able to run the installer (as well as gparted) from a flash drive. 

thanks
josh

---

### Post by markitect on 2007-03-14
You should be able to turn a flash drive into a live CD no problem.  Just make sure that the flash drive is bigger then the cd, download the image and do 
```
 dd if=ubuntu.iso of=/dev/sd?? 
```
where the of= has the location where your computer mounts the usb drive from.
and youll need to unmount the filesystem of the flashdrive beforehand

---

### Post by phantommaggot on 2007-03-15
sweet, ill give that a try. 

im gonna buy the tablet next month, but ill get a flash drive in the next couple weeks..


THANKS!
that was awsome help

---


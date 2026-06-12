---
title: "Keeping my /home partition"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by pgibson on 2010-11-07
When I installed 9.04, I set up a separate /home partition. I want to keep that /home partition now that it's time to upgrade to 10.04.1 LTS.   I've found a lot written about creating a separate /home partition, but I can't find anything about the reverse process: doing a clean install on the OS without losing the info on the "/home." Here's what I've done to prepare:

[LIST]
[*]I've backed up everything with simple backup and moved it off this machine;
[*]furthermore, I've copied her documents, photos, and several config files (such as .mozilla and like that) to another computer
[*]I've got the 10.04.1 cd spinning in her machine, awaiting my instructions.
[*]I've noted which partitions are which by their ID number
[/LIST]

So I have two questions immediately pressing on me:

[LIST=1]
[*]Using the manual installer, shall I flag the old 9.04 partition as a new "/" ?  (or possibly "/boot"?)

[*]And do I need to flag the partition currently labled "/home" as "/home" again?  Or will the installer read that somehow?
[/LIST]

Thanks as always.  10.04.1 is amazing!  I swear the live CD seems almost as fast as 9.04 on the hard drive (on my daughter's old IBM T30).

Yay.

---

### Post by cpmman on 2010-11-07
Specify your / as / and **format**

Specify /home as /home but do **NOT** format

---

### Post by dino99 on 2010-11-07
on standard installation you might have 3 partitions:

- / : root bootable with ext3 or ext4 format, about 12~15 Gb; its where 9.04 is actually installed. If you want a fresh 10.10 install, then you will format it first (you are automatically asked by the installer IF you you install from the "alternate" iso, you have to know its name (/dev/sd?) to be sure to format the good partition of course)

- swap: ~ 2Gb

- /home: all the space you want, ext3 or ext4 format. On that partition your data and settings are safe IF you dont format it, only be carefull.

*** note: if /home is a folder and not a partition: then create a /home partition and copy/paste your /home folder into it.

---

### Post by pgibson on 2010-11-07
Cpmman and Dino, thank you.  You are both rock stars!:guitar:

---


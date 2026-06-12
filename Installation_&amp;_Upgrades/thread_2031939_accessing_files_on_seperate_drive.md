---
title: "accessing files on seperate drive"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by tim.hoeffel on 2012-07-22
So I had some help an successfully have a dual boot system with Win 7 and 12.04 LTS installed on one drive (200GB). My other drive is a 1 TB drive with all my files on it. I was hoping to be able to access (read/write) my files from ether system, but that is not possible yet. Looks like a raid array is how to build that bridge. Any advise on which kind of array to use and a good reference for doing it?

---

### Post by Paddy Landau on 2012-07-23
We need some more information.

How is the drive formatted (e.g. NTFS)?
Can you access the drive from Windows?
Can you access the drive from Ubuntu?
Is it a USB drive, internal to the computer, or something else?

Also, open a terminal (in Ubuntu) with your 1TB drive attached, type the following command, and post the results here between [FONT="Lucida Console"][noparse]```
[/noparse][/FONT] and [FONT="Lucida Console"][noparse]
```[/noparse][/FONT].
```
sudo parted --list
```

---


---
title: "help me install 8.10 from iso on hd (xp user)"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by pagaNs on 2008-11-10
I'm a bit lost, was looking all over the net and haven't found anything that would guide me through this process. I have used ubuntu earlier and I like it. Right now I have only xp installed with hd of 40GB, c:10GB and d:30GB .
The thing is my older brother have iso image of 8.10 but i dont have DVD reader. I was thinking if it would be possible to get it via ftp on my hd, and prepare everything to boot from hd, to install it just like from CD. Unpluging his DVD is not an option.
PLEASE!!!
Point me to guide or guide me to:
install 8.10 from iso image on my hd.
I want to know do i need to reformat one partition to ext3 before saving iso on hd, how to prepare it for install, what to do to get grub and everything else working, so finally i could get the same result as installing via CD.
Tnx everyone...

---

### Post by logos34 on 2008-11-10
here you go:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Since you already have the .iso, simply select the disk image option and path to iso file, type (HDD) and drive/target installation partition (you'll obviously have to shrink your D: drive down beforehand and create a new ext3 partition from the freed space):
> **Installation & Screenshots**

  Before installing, remember to back up all your data, in case you do something wrong in the partitioning stage of the installer.
 If using Windows, run the file, select a distribution, floppy/hard disk image, or kernel/initrd to load, select a target drive (HDD/USB), then reboot once done.

[IMG]http://sourceforge.net/dbimage.php?id=173795[/IMG]


good luck

---

### Post by pagaNs on 2008-11-10
**tnx a lot friend**,
in the mean time, I was trying to install from live CD(DVD)...
had no success, after choosing language, loading kernel starts, and then that #### prompt, removed splash and quiet and got the last line "Uniform CD-driver revision.." where the process stops before giving me the busybox...
looking for hours now, and cant find solution, at the end I might do as I wanted in the first place, install from hd

...just was inpatient to wait for answer, and wanted to try to make a clean instal without win stuff

---


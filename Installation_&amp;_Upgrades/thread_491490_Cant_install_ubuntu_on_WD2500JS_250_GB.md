---
title: "Cant install ubuntu on WD2500JS 250 GB"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by yarayara on 2007-07-03
Hi,

I tried to install the ubuntu 7.04 desktop and later the server.

in the first try, I couldnt set up the partitions because it simply didnt show anything, so I couldnt.

with the server, it says it does not find a hard drive.

Mine is a Western Digital Caviar® SE WD2500JS 250 GB.

I cant find the driver. maybe if someone could point it out, I could copy it on the drivers folder and then burn the distro again.

could that work? or what should I do? I dont have a floppy drive.

thanks.
-yarayara

---

### Post by dabl on 2007-07-03
To deal with the partitioning thing, download and burn the GParted Live CD ISO from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot your GParted Live CD, and use it to make partition for /, /home, and /{swap}.  I don't know how much RAM you have, but a pretty safe bet would be:

/ = 10 GB
/{swap} = 1GB
/home = all the rest of it

The mount points (/, /{swap}, and /home} will not be assigned by GParted, but you need 3 partitions of those sizes, and you need to set the "bootable" flag on the 10 GB partiition.

Next, boot the Ubuntu 7.04 Alternate Install CD.  Use "guided installation" and you don't need to partition. Just select the mount points as per the above plan, and let the installer format the partitions.  I like reiserfs, but you can use ext3 just as well, except for /{swap} which will use its own format.

I hope this gets you going!  :)

---

### Post by yarayara on 2007-07-03
seems good!

Im downloading the gparted.

something else.

I have a second hard drive, exactly the same, but Ive installed windows XP. How should I manage the dual boot if I have windows in 1 disk and ubuntu in  another?

thanks,
-yarayara

---

### Post by yarayara on 2007-07-03
well, I tried the GParted live, versions 3.4.8 (last one) and 3.4.7 and neither go to graphical mode, like in the tutorials Ive found.

I get to the line #newroot>

or something like that..

any guess?

thanks

---

### Post by yarayara on 2007-07-04
any ideas on this one?

Ubuntu installation starts ok but it does not detects the disk, and gparter wont go to graphic mode  :S

what to do??

thanks!

---


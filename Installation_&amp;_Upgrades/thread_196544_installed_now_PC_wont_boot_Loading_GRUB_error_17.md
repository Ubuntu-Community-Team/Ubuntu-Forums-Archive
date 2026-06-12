---
title: "installed now PC wont boot: Loading GRUB error 17"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by trent31 on 2006-06-14
please somebody help me. im very new to this. i went through the whole install process and created a new partition with freespace in the installer. (i have one HDD)
now when i boot up it says loading GRUB    error 17
i cant work out how to do anything but but boot the live CD
i cant afford to lose my windows files as i havent backed everything up (stupid i know)
even in the live cd i cant access the HDD, it just says
Unable to mount the selected volume.
error: device /dev/hda2 is not removable

error: could not execute pmount

sometimes the partition where i believe ubuntu is has the same error, other times it says
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-hda1".
can anyone help me at least get windows back???
im desperate, im stressing out here as im meant to be getting up for work in a few hours and cant sleep till this is fixed. searched the forum but i cant find anything. the rest i dont really understand....

SOMEBODY PLEASE HELP

---

### Post by John.Michael.Kane on 2006-06-14
A grub error of 17 means:

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

If you can try reinstalling ubuntu from the beginning. when you get to the partitioning section of the install re-select the your ubuntu partition, and swap. it should give you the option to format to keep data or format you want to format the ext3 partition, and let the setup reinstall. it should also find your windows install, and ask if you want to add it to grub menu you will select yes. it will continue installing. this is the method i have used with out issues. however i can't guarantee it will work sine i don't know how messed up your install is.


Sidenote: you should be able to use a livecd mount your drive, and back your data up to dvd or  external hd.

---

### Post by trent31 on 2006-06-18
All good now. Cheers.

---


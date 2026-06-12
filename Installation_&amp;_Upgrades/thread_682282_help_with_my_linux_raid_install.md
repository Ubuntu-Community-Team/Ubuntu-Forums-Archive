---
title: "help with my linux raid install"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by keithacole on 2008-01-29
i have attatched an image representing my harddrives and the partitions i want to use

ive read howto's and tutorials on how to set the raid up, my question is would this setup benefit me with performance and safety from loss data

i was thinking linux software raid 5 with this

[IMG]http://keithacole.googlepages.com/LINUXRAID.JPG[/IMG]

i would be booting to the 500GB drive, thats why /boot is on there.

questions are:

when i add more 500GB drives to replace the smaller drives, can i do this without totally reinstalling the distro?

the ARCHOS partition is a mirror of my Archos605 160GB

---

### Post by keithacole on 2008-01-30
i learned that you can not have more then 4 partitions on any 1 drive, so i've resized the 160GB partition to use the entire space, and moved the /boot over to the 40GB drive and reduced all the /home partitions to 38GB so that they are all the same size..


i still havent started the install yet becuase the drives are being clean with dban's disk nuke

---

### Post by keithacole on 2008-01-30
ok, i got info that i need to make the 4th partition logical, and subpartition that.

i also found that LVM is what would allow me to expand to extra disks without messing everytihng up

---


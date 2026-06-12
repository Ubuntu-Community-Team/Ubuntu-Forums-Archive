---
title: "Help - Turn off U9.04 forced filesystem check completely - how ?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by jenaniston on 2010-01-28
I figure I am definitely lucky to get *anything* from a USB Ubuntu 9.04 installed 
via a campus Dell - and then run on a " broken" Sharp AL27 laptop - 
I am trying to rescue files off the unbootable Windows XP FAT32 partition.
 
After the **25th** mount - while still working on getting this USB OS working better on the laptop -
I *now* have to start it all over again - filesystem check fails and won't boot on eithe r the Dell or Sharp laptop now.
 
I understand the - usually desirable - system filecheck ***can*** be turned off completely.
[http://blog.dipinkrishna.info/2008/11/ubuntu-30-mount-check-annoyance.html](http://blog.dipinkrishna.info/2008/11/ubuntu-30-mount-check-annoyance.html)
 
I need to do exactly that for this temporary, but very useful, "jerry-rig" USB pendrive OS installation -
at least for a while before I can install over Windows completely.
 
How can I do that please ? 
Running in terminal mode as root is about all I can do on the laptop,
although the Jaunty desktop was starting to come more to life (fix USB mouse etc.) 
 
Thank you very much.

---

### Post by doas777 on 2010-01-28
in your /etc/fstab file, you will notice two numbers on the end of each line. change the last number to 0, and the volume will not be scanned. if you do want it scanned, use a number greater than 0, that is the order in which you want your disks checked.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by jenaniston on 2010-01-28
> **doas777 said:**
> . . . /etc/fstab file, you will notice two numbers on the end of each line. change the last number to 0, and the volume will not be scanned. . . .
 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
 
Excellent info on the fstab options . . .
 
This will also be very important to me after I get all this back set-up again . . 
 
I'll check to see how etc/fstab lists those laptop Windows XP partitions . . . 
the one 25 GB extended FAT32 partition mounted *automatically* on my U9.04 jerry-rig USB OS Jaunty Desktop -
but the 35 GB primary partition did NOT (and I'll worry if it is even able to be mountable) - 
that is the partition with the "broken" XP OS and the files I want rescued. 
 
The **parted** utility did NOT recognize that sick partition as even *having* a filesystem or a boot flag,
while **sfdisk -l** and **fdisk -l** *did *list the primary partition as FAT32 with boot flag - 
these fstab settings may help explain why there was a difference between how
the partition utilities recognize the disk "slices" (borrowing unix terminology).
I hope that is all it is.
 
Thank you very much.

---


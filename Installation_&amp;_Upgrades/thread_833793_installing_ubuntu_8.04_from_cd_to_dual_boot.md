---
title: "installing ubuntu 8.04 from cd to dual boot"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by biteme138 on 2008-06-18
hey i'm a complete beginner with ubuntu - trying to install it off a cd n having some problems...

i have 2 hdd's - one with windows xp installed on it, another thats been split into 2 logical drives (this is the one i'm trying to install on :()

in the 2nd hdd, its split into a big partition(needed for work in xp) n a 20gb partition that i've split into 8gb for swap n the rest for root.

in the final step these are the settings:
"The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #5 of SCSI3 (0,0,0) (sda) as swap
 partition #6 of SCSI3 (0,0,0) (sda) as ext3"

when i try to run it i get this:
"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/Games\ & Programs&\ ProgramsPrograms

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"
not sure what to do....

---

### Post by cdtech on 2008-06-18
The safest way is to remove or disconnect your windows drive and connect your second drive as primary (I recommend this as a new user). Your swap partion is overkill, the most you would probably need is 2G (from my experiance).

I would let the install CD format your drive and automate all the partitions you would need. Sounds like your having issues with the windows hard drive.

According to the message your getting, the installer wants to format your windows drive. sda is drive one (primary) and sdb is drive two (secondary).

Hope this helps......

---


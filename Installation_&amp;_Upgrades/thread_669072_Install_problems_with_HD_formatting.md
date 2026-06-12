---
title: "Install problems with HD formatting"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by shiznatix on 2008-01-16
My friend installed ubuntu on his laptop but after his mother complained about not being able to use (insert random windows program) she took it to a computer support store to get windows put back on it.

Well the guy who tried to put windows on it was unable to "uninstall linux" for whatever reason and then gave the computer back with no windows on it and no linux on it. My friend gave me the laptop to look at, I tried to just put Ubuntu back on it but when I get to the step in the installation where it actually tries to format the drive, I get this error:
> The creation of swap space in partiion #5 of SCSl1 (0,0,0) (sda) failed.

I have the settings set to manually partition the entire disk so I don't know what all of the partitions are since Ubuntu is making them for me but thats where it stops and fails. If someone has any idea about what to do with this please let me know.

---

### Post by overdrank on 2008-01-16
> **shiznatix said:**
> My friend installed ubuntu on his laptop but after his mother complained about not being able to use (insert random windows program) she took it to a computer support store to get windows put back on it.

Well the guy who tried to put windows on it was unable to "uninstall linux" for whatever reason and then gave the computer back with no windows on it and no linux on it. My friend gave me the laptop to look at, I tried to just put Ubuntu back on it but when I get to the step in the installation where it actually tries to format the drive, I get this error:


I have the settings set to manually partition the entire disk so I don't know what all of the partitions are since Ubuntu is making them for me but thats where it stops and fails. If someone has any idea about what to do with this please let me know.

HI and you can try to use gparted on the live cd under system, administration and just delete all existing partition on the drive then reboot and try again. Hope this helps and good luck!

---

### Post by shiznatix on 2008-01-16
I have tried doing that but when I get into gParted it says that the whole disk is unalocated disk space so it does not have any partitions on it or anything like that. When I try to create a new partition on it, it tries to set a disk label but I get the error "Error while setting new disk label" and thats it.

Any other ideas?

---

### Post by c0met on 2008-01-16
Have you booted from a live CD and tried to format the hard drive using Terminal? The command is mkfs and you'd probably need to add sudo at the front of it.

e.g. sudo mkfs -t ext2 /dev/hda

(this is assuming that your hard drive is hda)

Below is a bit of information about using mkfs. 

[http://www.linfo.org/mkfs.html]("http://www.linfo.org/mkfs.html")

---


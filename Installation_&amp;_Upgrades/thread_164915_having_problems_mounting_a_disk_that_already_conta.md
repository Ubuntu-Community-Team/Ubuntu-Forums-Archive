---
title: "having problems mounting a disk that already contains a ubuntu install"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by sybariten on 2006-04-23
Had a Ubuntu PPC system running on a Mac, from a single IBM 70 gb harddrive.
Ripped that disk out, set another Ubuntu (server) up on a normal PC. Used a 3.5 gb Maxtor drive there. Think its jumpered to master. It boots up and runs nicely. Added the IBM HD to the same IDE chain, want to mount it in the new PC ubuntu server. 
Dont know what partition to use. **Is this reccommended at all? **It would make sense to format the drive to get rid of all of the OS files, but i already have like 40 gb of other files on it. Figured i could just rm /etc, /usr, /bin, /sbin etc (!) from the IBM drive once i get it mounted.
But fdisk -l just shows the 3.5 gb drive. For the other drive, it says "/dev/hdb doesnt have a valid partition table". 
The new 3gb system is EXT3, the 70gb one i want to mount is EXT2.

Any ideas?

edit: some dumps: [http://pastebin.ca/raw/50773](http://pastebin.ca/raw/50773)

---

### Post by sybariten on 2006-04-24
Update:
I got word that the big disk might be feckud up since fdisk gave so bad reports when doing some tests. So i removed the disk and put it back into the iMac. Works like a charm. Phew.
Tried taking another, smaller disk, and adding it to the same end of the IDE cable from the server
(in other words: i put a 4 gb drive at the place where i had tried the 70 gb drive, in the server) Worked like a charm. That 4gb drive also had an installed linux system, but i could mount it like a slave drive without problems.
Reinstalled the 70 gb disk again, but checked the jumper settings. It is, as i said, at the end of the IDE flat cable. The jumpers look like this:
[http://www.hitachigst.com/hdd/support/dtla/dtlajum.htm](http://www.hitachigst.com/hdd/support/dtla/dtlajum.htm)
Look for the left illustration in the 2nd row (Device 1 slave, 16heads)

sudo fdisk -l gives

[QUOTE=linux]Disk /dev/hda: 3510 MB, 3510308864 bytes
255 heads, 63 sectors/track, 426 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         404     3245098+  83  Linux
/dev/hda2             405         426      176715    5  Extended
/dev/hda5             405         426      176683+  82  Linux swap / Solaris

Disk /dev/hdb: 76.8 GB, 76869918720 bytes
16 heads, 63 sectors/track, 148945 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

[COLOR="Red"]Disk /dev/hdb doesn't contain a valid partition table[/COLOR]
[/QUOTE]

---


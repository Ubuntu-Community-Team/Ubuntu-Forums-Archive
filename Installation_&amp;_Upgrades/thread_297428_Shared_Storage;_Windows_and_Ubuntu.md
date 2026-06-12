---
title: "Shared Storage; Windows and Ubuntu"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by SilentDeath on 2006-11-11
I'm inquiring about how I can make my storage drive from windows usable by Ubuntu. It already sees the hard disk, but I cannot write to it. I've set this up so I really don't have to worry about loosing files if for some reason Linux or Windows takes a dump on me. I can just reformat their installation partitions and have all my data. So I would like to be able to actually use this storage drive instead of just being limited to read only.

So is there anyways I can add/alter data on this drive without being logged in as root or using sudo??

---

### Post by bulldog on 2006-11-11
Well you can make the storage FAT32,so you be able to use it with windows and ubuntu as well.

Ubuntu can read NTFS but not write to it by default.
That could be changed but I won't recommend it,like others do.

I have a very bad experience with it in the past,so I don't try it again.

---

### Post by funkyade on 2006-11-11
Is this a completely separate drive or a partition? Is it using NTFS? Is it on the same computer or on a different computer on a network?

You should be able to share the drive easily using Samba if it's on another machine and it is turned on. If it's on the same machine you will need to mount the drive at boot, by adding an entry to your /etc/fstab file. Linux can read and write to NTFS partitions, however, windows will have difficulty reading your linux ones...

hth

++ do second the NTFS warning above. Is more reliable using networked storage formatted as JFS or similar, and letting windoze access it as a shared network drive.

---

### Post by tribaal on 2006-11-11
Ntfs drivers exist for Ubuntu, but they are to be considered experimental (you have a slight risk of loosing data).

Why not go the other way around? Install an ext3 module on your windows machine? I believe this is more robust, as ext3 is a journaling filesystem that can be read/written by both, while FAT32 is non-journaling (you risk loosing stuff in the event of a crash).

Just my 2c...

- trib'

---

### Post by happy-and-lost on 2006-11-11
On your Windows install, get the "TweakUI" powertool from M$ downloads. This will allow you to redirect your "My Documents" folder to another drive (i.e. your E: FAT32 drive), just make sure you copy the contents of "My Documents" over to it first!

---

### Post by SilentDeath on 2006-11-11
Well, the hard disk is in the same machine. I just have it set up as: 92.7Gig partition for windows, a 778.15MB swap, and another 92.7Gig for Ubuntu. The other hard drive is just another JBOD on my nforce4 raid controller. Its identical to my primary with about 185 Gig total allocation. I'm not worried to much about the data of the drive as I just set this up, only a few files on it. How would I go about formatting the drive as a ex3 journaling and being able to use read and write to it in windows and Linux?

---


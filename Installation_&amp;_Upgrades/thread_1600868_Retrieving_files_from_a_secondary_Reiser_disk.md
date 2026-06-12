---
title: "Retrieving files from a secondary Reiser disk"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by jharan on 2010-10-19
Hi,

I've been running various releases of Suse Linux on my home PC for about 6 years (currently running Suse 11.2). The old hard disk in that machine is starting to experience read errors, so I bought a new disk to put into the PC which otherwise works fine.

So I figure now is a good time to give Ubuntu a try. I plan to install the KDE version of ubuntu on the new drive, but once that's finished I will want to mount the old disk and copy as much as I can off of it onto the new disk (JPEGs, old documents, stuff under my home directory.

The old disk uses Reiser. I have read various threads concerning problems with mounting Reiser FS disks under ubuntu, but many of them are old so it's not clear to me what the current status of support for Reiser in ubuntu is.

I am planning to do the following:

1) Remove the old disk from the PC, put the new disk in its place.
2) Install kubuntu on the new disk.
3) Put the old disk back into the machine along with the new one with the old one being the slave/secondary disk so that when I power up the machine, it will be running ubuntu off of the new disk.

At this point I will want to mount the old disk so I can then start copying files off of it.

What do I need to do to mount the old disk, keeping in mind it uses the Reiser file system?

Specificity would be appreciated. The exact invocation of mount to make this happen would be nice.

Thanks in advance.

---

### Post by lemming465 on 2010-10-21
I would expect reading a reiserfs formatted filesystem to just work, and the regular mount command to recognize the filesystem.  So I'd try either a) pick the ReiserFS filesytems off the "Places" menu, or do ```
sudo -i
cd /media
blkid
mkdir sdb1 sdb2 ... # how ever many you need
mount /dev/sdb1 sdb1
mount /dev/sdb2 sdb2
# etc.
```
and then just copy files with "cp -r" or something.

---


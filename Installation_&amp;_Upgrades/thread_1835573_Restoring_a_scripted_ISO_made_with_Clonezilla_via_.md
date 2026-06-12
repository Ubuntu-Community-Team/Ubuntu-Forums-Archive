---
title: "Restoring a scripted ISO made with Clonezilla via Grub2 menu"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by MicroWha?LinuxFTW on 2011-08-29
Howdy!

Here's my problem.

I have 20 laptops for training purposes. All set up the same way. 500 gig harddrive, split into 4 primary partitions.

---
SDA1 - EXT3 - 20 gig Ubuntu 10.04 - Also has the original Clonezilla ISO (the bootable download)

SDA2 - NTFS - 100 gig XP

SDA3 - EXT3 - 100 gig Ubuntu 10.04 (yes... another copy of Ubuntu 10.04)

SDA4 - EXT4 - 220ish gigs - Storage for Clonezilla backups - currently holds a backup image of SDA2 made with Clonezilla, and that same image also provisioned as a bootable ISO (normally to be place on a bootable USB key or DVD... however, the ISO is to large for either).
----

Currently, my Grub2 loader allows me to...
1) Boot Ubuntu 10.04 on SDA1
2) Boot Clonezilla ISO on SDA1 (this boots a 'clean' Clonezilla)
3) Boot XP on SDA2 (NTFS)
4) Boot Ubuntu 10.04 on SDA3


In training, when students mess up their XP image, I'm forced to boot Clonezilla from my grub2 menu, choose to restore the backup image I've taken of SDA2, pick all the necessary choices and restore it.

This manual way of restoring the SDA2 image is so tedious, and takes way to long.

Now... Clonezilla allows you to turn a restoration image into a bootable ISO. As aforementioned, I have done this, the ISO is currently residing on the SDA4 partition.

What I WANT is a 'Restore XP Image' within my grub2 menu. When selected, I want it to restore the SDA2 partition (XP). I don't care how it's done, but I figure it can be done 1 of 2 ways...

EITHER

:BOOTABLE ISO METHOD:
1) Grub2 boots the restoration ISO on my SDA4 partition, as it would if I had burnt this ISO to a recovery USB or DVD- with all choices fully scripted. Thus removing human user error factor.

--OR--

:CLONEZILLA IMAGE METHOD:
2) Boot Clonezilla in such a way, that Clonezilla is scripted to choose the appropriate image, and restores it to SDA2.

Again. I just want to make a selection on my grub2 menu, and hit 'y' a few times. I don't want to make selections in Clonezilla every time.

What I'm looking for is help writing the code to provision the 'custom' file in my grub2 menu. I can't seem to figure out how to boot an iso from my 4th partition, nor can I figure out how to pass along scripted instructions to Clonezilla.

Thanks ahead of time!

---


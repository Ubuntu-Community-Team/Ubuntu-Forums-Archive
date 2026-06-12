---
title: "Want to change partition labels"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by brucenduane on 2006-06-11
I have 3 drives on my Ubuntu Dapper desktop computer.
AMD 2.6 Ghz 1 gig ram
2 Parallel ATA drives 80 gig and 40 gig with 4 partitions 1,2,3,4
1 160 gig SATA with 11 partitions 6-reisierfs  4-ext3  1-vfat

Problem:   
In Ubuntu Breezy 5.10 the SATA drive partitions are labeled in the desktop icons
sda1, sda2, .... sda10, sda11.
I can live with that and have a yellow sticky note on my physical desk to translate that into my partition usage of music, video, Dapper, Breezy, Puppy, iso, vfat, .... etc

In Ubuntu Dapper the SATA drive partition icons on the desktop are labeled
Debian, Knoppix, Mandriva, /media/sda8, Music, sda01, sda09, /Ubuntu

Thats nice but:
Dapper is installed in the icon partition labeled "Debian"
Breezy is in the icon labeled "Knoppix"
Music really in the icon "Mandriva"
iso's are stored in the icon labeled "/Ubuntu"
databases is stored in icon labeled "Music"

I labeled the partitions with one of the distribution installers, I don't remember which one.  At one point I have 8 distributions on this drive.  Anyway I only have CD/DVDs for Chubby Puppy 1.05, Puppy 2.00, Ubuntu 5.10 & 6.06, Mandriva 2006, Knoppix 4.04, and GParted 0.2.4.2 LiveCD.  None of these distribution partitioner's seem to be able to set partition labels that I am aware of.

Questions:
How do I change the partition labels on the reiserfs partitions?
How do I change the partition labels on the ext3 partitions?
How do I change the partition labels on the vfat partitions?
                                                  or
Can I change the simply change the icon labels on the desktop?

---

### Post by kaamos on 2006-06-11
[QUOTE=brucenduane]
Can I change the simply change the icon labels on the desktop?[/QUOTE]

Yes, the desktop label is the same as the name of the mountpoint. So if partition /dev/hda4 is mounted at /media/blaablaa, there will be a label "blaablaa" on your desktop.

Create folders with what you think have better names under /media/ and use
```
sudo gedit /etc/fstab
``` to change the mount points.

---

### Post by brucenduane on 2006-06-11
I know about changing the mount points and fstab.  That doesn't appear to make any difference in the icon label since I have no mount point or directory labeled "Debian".

The desktop icon is labeled  "Debian" and the mount point is /media/sda1 or device /dev/sda1.    My question is:  How do I change the "Debian" to "sda1" on the desktop icon?

Thank you for your quick response.  -Bruce.

---

### Post by brucenduane on 2006-06-19
Problem solved:

Used e2label to change the ext2 & ext3 partiton labels.
Used reiserfstune to change the reiserfs partition labels.

-Bruce.

---


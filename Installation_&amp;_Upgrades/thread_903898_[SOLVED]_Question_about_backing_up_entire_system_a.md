---
title: "[SOLVED] Question about backing up entire system and multibooting"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by super.rad on 2008-08-28
Not really a qustion about installing/upgrading but felt it was best to post here.
I currently dual boot Ubuntu & Arch, I want to install Gentoo aswell but I need to wipe my hard drive and create a new partition table.
I've spent quite a while setting up both Ubuntu & Arch just the way I want them with all the programs I want aswell. I don't want to reinstall them both as it'll take me ages to setup both as they were (especially arch as it took over 4 hours to download Xorg, Gnome, etc)
What I want to know is would I be able to just copy the / partition of both to a backup drive, repartition my hd and then copy them back (I know i will have to edit fstab to point to the new partitions)
If I booted onto a live cd could I just do the following for both ubuntu and arch?
```
sudo cp -a /location/of/ubuntu /location/of/backup/drive
```
repartition my hard drive then from a live cd
```
sudo cp -a /location/of/ubuntu/backup /location/of/new/ubuntu
```
Then edit fstab for both and grub.
Also would this work for a patition layout
Primary Partition #1 - 10GB Ubuntu /
Primary Partition #2 - 10GB Arch /
Primary Partition #3 - 10GB Gentoo /
Extended Partition
Logical Partition #1 - 2GB SWAP
Logical Partition #1 - Rest of HD shared /home (different usernames for all 3)
Any help would be much appreciated. Thanks

EDIT: After asking on IRC I got the answer

---


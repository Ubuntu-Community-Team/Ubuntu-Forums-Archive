---
title: "[SOLVED] How to move NTFS partition?"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by sci-fi guy on 2007-06-30
I dual-boot my laptop, so when I installed Ubuntu I resized a NTFS partition rather than deleting it. I later realized (after installing Gnome partition editor) that Toshiba had a "recovery" partition for if Vista had to be reinstalled.  This partition was about 1.5 GB (for 100MB of data), and I decided to delete it.  Unfortunately, on the disk the partitions were organized as

| (recovery partition-1.5GB) (Vista NTFS-54GB) (Ubuntu-54GB) (Swap-2gb) |

Now I have 1.5 GB of empty space on the far side of my Vista install, and would like to move the Vista install into that space so that I can expand my Ubuntu without making a new partition. The partition editor (Gparted) does not seem to be capable of this. Can Vista do this? Is there a partition editor for Ubuntu that can do this?

---


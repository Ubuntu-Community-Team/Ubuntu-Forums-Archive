---
title: "Partitioning failing on D600 Latitude"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by dshimer on 2011-01-25
I have installed a dozen dual boot XP / Ubuntu boxes, however this one has me stumped. After the installation failed in the partitioning phase I tried manually partitioning which also failed. Then I went to using a Gparted LiveCD. I can resize the NTFS partition fine each time rebooting in XP and it is OK. However when I shrink the NTFS then try to add an ext4 (or ext3) right after the NTFS it acts like it is working, then when it says "complete" the disk disappears out of Gparted and it shows no devices. If I reboot into the LiveCD it shows a blank second partition, if I try to format it in ext4 I get the exact same results. If I go to Windows it will show an unknown healthy partition. If I grow the NTFS back to the full 60Gb it seems to work fine. It just won't create a second primary ext4 partition.
Any ideas on where to go next?

---

### Post by srs5694 on 2011-01-25
Abandon the GUI tools, which have very poor diagnostic and error-handling features. Boot to a live CD and launch a Terminal program. Post the output of the following commands, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

These commands will display technical details about your hard disks and partitions, which should be useful in diagnosing the problem, and ultimately fixing it. You may need to use fdisk to create partitions and/or use tools like mkfs and mkswap to prepare them for use.

---


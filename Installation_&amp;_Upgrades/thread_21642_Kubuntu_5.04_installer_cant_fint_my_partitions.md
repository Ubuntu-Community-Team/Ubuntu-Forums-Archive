---
title: "Kubuntu 5.04 installer cant fint my partitions"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by KDE-fan on 2005-03-23
I recently tried the Kubuntu5.04 live-CD, and liked it so much that I decided to install it on my hard drive. I therefore downloaded the proper installation CD, and the installation process went fast and smoothly until I got to the partitioner. It simply didnt find my partitions! It did find my harddrive though, but it didnt feel like erasing everything on it. I therefore stopped installingt, and am currently using Mandrake 10.0 Official again.

My disc have the following partitions that the installer didnt find. I have put them in the same order as the appear on the disc.

hda5, / , ext3 , 4.5 GB
hda1, linux swap, 2.4 GB
hda6, /home, ext2, 9.4 GB
hda7, /mnt/StorDisk, reiserfs, 58 GB

Any solutions?

---

### Post by KDE-fan on 2005-03-23
I now see that 5.0.4 has its own section. Can someone pleace move this thread?

---

### Post by KDE-fan on 2005-03-23
Problem solved! This is how I did it: 
1. Deleted the two first partitions with Mandrake-10.2-RC1-Mini-CD (/ and swap)
2. Recreated them with the same CD.
3. Booted with KubuntuCD.

KDE 3.4 looks great, but I still have to do some work with the fstab-file. That is a minor issue though.

---


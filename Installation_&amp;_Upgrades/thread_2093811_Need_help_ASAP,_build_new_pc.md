---
title: "Need help ASAP, build new pc"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Sabbra on 2012-12-11
ok so i got 2 problems, i built a new pc and it has no OS yet, so i  put my old hdd to my new pc because it needed one, and i ran the disk to install ubuntu but it says that i only have 3gbs left and it needs 4.9, i have more than 3gbs (500gbs to be exact) and im running ubuntu on the try it out mode, i need help on this

the second one is my destop dosent fit my screen i have no idea how to fix it.

---

### Post by Herman on 2012-12-11
> i built a new pc and it has no OS yet, so i  put my old hdd to my new pc  because it needed one, and i ran the disk to install ubuntu but it says  that i only have 3gbs left and it needs 4.9, i have more than 3gbs  (500gbs to be exact) and im running ubuntu on the try it out mode, i  need help on this If I'm understanding you right and jumping to the correct conclusions, you probably need to back up your data to another disk of some kind and then either delete one or more partitions or at least resize smaller to make room for Ubuntu. GParted in the LiveCD or USB is the best program for working with partitions, and the partitioner that's built into the Ubuntu installer is equally capable. You can probably 'see' what you're doing easier in GParted. 
> the second one is my destop dosent fit my screen i have no idea how to fix it.     Go into 'System Settings', and open 'Displays' and you will find the settings there.

---

### Post by Wim Sturkenboom on 2012-12-12
> **Sabbra said:**
> ok so i got 2 problems, i built a new pc and it has no OS yet, so i  put my old hdd to my new pc because it needed one, and i ran the disk to install ubuntu but it says that i only have 3gbs left and it needs 4.9, i have more than 3gbs (500gbs to be exact) and im running ubuntu on the try it out mode, i need help on this

You can post the output of _sudo fdisk -l_ (that's a lower case L at the end). It will show us which partitions you have. Your current partitioning scheme might be a 5GB root partition, a 4GB swap partition and 491GB allocated to your home partition. So there will indeed no space for another Ubuntu install, even if there is 400GB free on the 491GB home partition. In the above scenario, you need to resize your 491GB to make space.

And a warning, give the root partition at least 10GB; it depends on how much software you're planning install how large that root partition needs to be; 25GB should be quite comfortable if you don't install too much and with 50GB you will never have to worry.

> **Sabbra said:**
> the second one is my destop dosent fit my screen i have no idea how to fix it.
You probably need to fine tune your X configuration; useless to do that in live mode, rather wait till you have Ubuntu installed.

---


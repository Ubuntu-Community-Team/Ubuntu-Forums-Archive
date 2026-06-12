---
title: "No partitions is visible from ubiquity"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Kwpolska on 2009-12-05
I want to install Kubuntu 9.10 on my SATA hard disk. I have it partitioned, i need to format one partition to ext3. When I'm in livecd, i can mount, unmount, browse and modify data on my partitions. fdisk, console herself and all KDE tools reporting that I have my partitions. But on installer or gparted there are NO partitions listed. I can in every while jump to Dolphin and see it. WTF with these tools?

---

### Post by darkod on 2009-12-05
Is the drive not listed at all or just the partitions? Boot up into the live environment and in terminal run:
sudo apt-get remove dmraid

In most cases like this there are some traces of raid on the drive and they will be removed.

---

### Post by Kwpolska on 2009-12-05
Failed. I'd got my disk partitioned like it:
```
XP - 20GB | L(ogical): Home - sixty-something GB | L: Linux - 30GB, formatted currently to NTFS | L: Backup - 37GB | L: Swap - 2GB
```
AlternateCD - same situation, but i don't tried to remove dmraid.

---

### Post by darkod on 2009-12-05
Try the dmraid remove with the standard LiveCD. It helped in this situations although I can't be sure that you have the same problem right now.

---

### Post by Kwpolska on 2009-12-05
I had tried it, no effect. If i will remove it and ubiquity, and try to install ubiquity, he is also downloading.

---

### Post by Kwpolska on 2009-12-06
Fedora had said me the right thing. Windows made something bad to my partition table. I need to recreate disk partitions.

---

### Post by thodpol on 2009-12-13
> **darkod said:**
> Is the drive not listed at all or just the partitions? Boot up into the live environment and in terminal run:
sudo apt-get remove dmraid

In most cases like this there are some traces of raid on the drive and they will be removed.


The drive was not listed at all.
with *sudo apt-get remove dmraid* and restarting the installation procedure, the disk is displayed in the partition editor!
Thanks a lot darkod! :)

---

### Post by djm-uk on 2009-12-13
Thanks - worked for me as well.  Thought it was a new drive but then remembered I had used it for testing on Hardware raid card.. strange that it leaves 'traces ' on the HDD that then stop installation though!

David

---


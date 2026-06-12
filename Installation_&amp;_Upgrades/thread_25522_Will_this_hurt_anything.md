---
title: "Will this hurt anything?"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by NateC on 2005-04-10
When I installed Ubuntu I had a Windows partition, but after using Ubuntu, and getting all of my windows games to work on Ubuntu I'd like to delete windows for good! If I insert the Hoary disc and go through the installation process up to partition editor, is it possible to delete windows and make my Linux partitions larger? And will I lose any information?

---

### Post by edubarr on 2005-04-10
You can change the type of parition by using cfdisk and then formating the disk to which ever filesystem you want (mkreiserfs for reiser, for example).

Just run 'sudo cfdisk /dev/hda' but be careful, you'll need to reinstall ubuntu if you delete the root partition.

---

### Post by NateC on 2005-04-10
Alright, I understand this. So resizing the linux partitions will not hurt anything, and Ubuntu will automatically notice the change in diskspace?

---

### Post by edubarr on 2005-04-10
[QUOTE=NateC]Alright, I understand this. So resizing the linux partitions will not hurt anything, and Ubuntu will automatically notice the change in diskspace?[/QUOTE]
 Don't resize the root parition, it's a bad idea. Actually resizing any partition will result in loosing data.

What you can do is add a new parition to your system, for example mount a partition called /games with your old windows one and have all your games in there or something similar.

---

### Post by edubarr on 2005-04-10
One thing you can do is run 'sudo fdisk -l /dev/hda' and show the output in here. This way it will be easier for me to help you out. Also specify which partition is what (your root and home for example, if they are on separate partitions).

---


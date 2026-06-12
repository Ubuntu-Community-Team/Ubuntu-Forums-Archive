---
title: "Partition Install Help Help Needed"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by Atonk on 2007-05-26
Hi,
I'm trying to install Feisty on my Dell Inspiron 1100 laptop. I currently have 6.06 and Mandriva installed (I tried to just upgrade to Feisty but I have problems with my adept manager).  Anyway, when I get to the disk partitioning section I select "use entire disk space." After that I get an error message saying "failed to create a file system - the ext3 system creation in partition #1 of SCS12 (0,0,0) (sda) failed."

What am I doing wrong? I'm not good at all with partitioning, so I don't want to just plug numbers in and possibly screw anything up beyond repair! Any help/suggestions would be greatly appreciated!
Thanks
Atonk:confused:

---

### Post by steevols on 2007-05-26
If you're trying to wipe Mandriva and 6.06, just load up the GParted CD (or the installer's advanced partitioner) and delete all the existing partitions. Then, make a new one, and set it to ext3 or reiserfs.

I think you can delete partitions on the installer by right-clicking on them and then deleting through the popup-menu.

---

### Post by coffeecat on 2007-05-26
> **steevols said:**
> just load up the GParted CD (or the installer's advanced partitioner)

**Atonk**, you can find Gparted under System > Administration > GNOME Partition Editor in the Feisty live CD Desktop. You can use that before you get into the installer if you want.

---

### Post by Atonk on 2007-05-27
This worked perfectly  - I'm so excited to finally have Feisty running on this laptop! Thank you so much to both of you -- I love Ubuntu and the community that comes with it!:biggrin:

---


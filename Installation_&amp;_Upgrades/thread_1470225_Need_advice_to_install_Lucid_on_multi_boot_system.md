---
title: "Need advice to install Lucid on multi boot system"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by VicVega on 2010-05-02
My current setup multi boots Hardy (8.04) on a drive (sda) that is partitioned for several versions of Linux and a second (sdb) drive that has only XP. I would like to install Lucid into one of the partitions on sda without borking my current setup. I want to keep Hardy.

The main question is: What to do with GRUB2 and my current GRUB legacy version. Also, will I need an additional swap partition for Lucid?

I like the fact that everything works well with Hardy. I rarely boot into XP and am not concerned about it that much. I have a separate partition for my personal files(Data) and HOME is in the root partition of Hardy. Attached is a picture of my partition setup. It is probably easier to visualize than to explain. 

I need advice on the best way to install Lucid and still be able to run Hardy with my current setup. I have search the forum and Google, but have not found a solution. I'm sure it can be done, I'm just not sure of the best way to do it. I hope someone can steer me in the right direction.

---

### Post by frantid on 2010-05-02
you don't need a different swap, just make sure you always do a restart between switching distros - i.e. don't switch when one is hibernated to the other one.

I installed everything in one partition, manually.  just choosing one partition for root.  Then I installed grub2 into the partition NOT the MBR.  This way I can chainload into lucid, test it out and it is pretty much isolated from the rest of my machine.

---

### Post by VicVega on 2010-05-02
Thanks for the response frantid. I'd like to hear from others on this too. 

Thanks

---


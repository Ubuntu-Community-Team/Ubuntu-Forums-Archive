---
title: "Installing another Linux"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by NoJock on 2006-02-19
Hello all:
I have windows and mepis working on my drive. I would like to also run ubuntu as well is it possable to deploy ubuntu to a partition already set aside for it on my drive and use the grub that is already running and installed. 

I hope this makes sence and i hope some one can help?

---

### Post by aysiu on 2006-02-19
No problem.

First **back up all your important data**.

Then, make a partition for Ubuntu. You'll need a live CD to do this--Mepis will work just fine. Just launch QTParted and then resize one of your existing partitions and create a new Ext3 partition. If you're resizing the Windows one, you may have to have it defragmented first.

Reboot with the Ubuntu installer CD in your drive and follow all the prompts. When you get to the partitioning part, select **Manually Edit the Partition Table**. Make sure you choose to format the newly created partition (don't accidentally select the Mepis or Windows partitions).

When asked if you want to install Grub to the MBR, say **no**.

Reboot into Mepis and click on the Ubuntu partition (which should be on your desktop) and open /boot/grub/menu.lst there (you may have to do this as root). Find the appropriate Ubuntu entry (usually the first one) and paste it into the Mepis /boot/grub/menu.lst (you will have to do this as root). Mepis' Grub has a slightly different format, but you can adjust the Ubuntu entry following the model of the other Mepis entries.

Save, and reboot.

---

### Post by NoJock on 2008-07-21
Thanks aysiu have moved on and using partiton magic now and just works.

---


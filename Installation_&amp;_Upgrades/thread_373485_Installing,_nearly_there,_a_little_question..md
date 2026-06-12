---
title: "Installing, nearly there, a little question."
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by tumble on 2007-03-01
Hi, so I managed to partition my usb disk and an on step five of installing ver 6.10, I'm not sure what to do on this page if anyone can help it would be great. It says:

Prepare mount points

Select which partitions you want to use for your new installation, and where you want to mount each of them.

You must mount one partition on the root file system ("/"), and you must choose at least one partition for use as swap space.

Then it has options and i dont know what to do?

---

### Post by Kateikyoushi on 2007-03-01
Hope this guide helps. [LINK]("http://www.psychocats.net/ubuntu/installing")

You need a swap partition about 1GB and a bigger / partition ext3 recommended, set the mount points accordingly.

---

### Post by desheikh on 2007-03-01
Hi,

The root partition ("/") is basically the partition that you want to install ubuntu to. You should have made a partition of about 2-3Gb at the very least for it, a bit more would be recommended for your own files and software. I recommend making an ext3 partition for it.

You dont really neeeeed to make a swap partition... if you have 1gb or so of ram and dont do very intensive tasks you can ignore it (youll get a warning when you do). I dont but on avg i people generally have 256 or 512mb swap partiotion. You need to create one in the partitioner and set the file system as linux-swap.

Mount points - In linux you mount partitions as folders in your linux directory... well kinda i think :P but basically what you do is pick the partitions for eg hda3 and type where you want them to appear in your linux drive eg /mypartition/drive3 (its all starts with "/" the root of ubuntu partition)
whatll happen now is that youll now access your partition (hda3) by going to the particular directory in this case /mypartition/drive3

Hope that kinda explains it :)

Ali

---

### Post by tumble on 2007-03-01
cheers folks thats good info

---


---
title: "Upgraded to Gutys, having two new problems"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by Scott_fakename on 2007-12-10
I decided to delete all of the partitions on my computer and except windows and put in ubuntu on the end, with an intermediat data partion in the middle (for future expansions purposes, not important).

Problem is that I now can't see my windows partition from linux, which I could in feisty. Also, I can't get windows to even see the linux partition, so I'm unable to add a virtual drive from windows.

How can I mount the Windows partition? Also how can I add a virtual drive from Linux? Preferably from the GUI, but if I must I will use parted or fdisk.

I looked it up in fdisk and all of those partitions exist. But I can't do anything with them.

--Scott

---

### Post by mikewhatever on 2007-12-10
If you see the Windows partition with fdisk, try [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by pieisgood4589 on 2007-12-10
You could try running the code (in bash, of course)
```

sudo cfdisk
```

And that usually recognizes all the Windows Partitions. Or, use GParted.

---

### Post by Scott_fakename on 2007-12-10
Ok, well windows found my Linux partition. So now the only problem is that I need to know how to mess with fstab without ruining anything. Is there a program that does that? Or do I just have to use gedit or pico or something?

Also I need to know what goes in there. Thanks for the replies,
--Scott

---

### Post by Partyboi2 on 2007-12-10
you can use gedit, I suggest to make a backup of your fstab file before you play with it.
something like this
```
sudo cp /etc/fstab /etc/fstab.bak
```

---


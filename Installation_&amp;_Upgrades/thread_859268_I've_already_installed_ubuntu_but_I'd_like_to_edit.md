---
title: "I've already installed ubuntu but I'd like to edit..."
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by nullbyte0 on 2008-07-14
my linux partition.  How would I do this?  Do I have to install gparted?  Or can I use whatever partitioning tool came default with ubuntu(I actually couldn't find out what the name of it was so I couldn't run it again)?

I'd like to expand my linux partition if that has any influence on what I need to do.

---

### Post by tuxxy on 2008-07-14
```
sudo apt-get install gparted
```

---

### Post by avtolle on 2008-07-14
You will need to boot from the Live CD, then when it comes up and you are at the desktop, do Alt+F2, in the box type gksudo gparted, press Enter, and that should put you into the partitioning application. The reason you need to use the Live CD is that the partition must be unmounted to do any work on it, and if trying to run from the HDD, the partition is, of course, mounted.

---

### Post by VMC on 2008-07-14
> **nullbyte0 said:**
> my linux partition.  How would I do this?  Do I have to install gparted?  Or can I use whatever partitioning tool came default with ubuntu(I actually couldn't find out what the name of it was so I couldn't run it again)?

I'd like to expand my linux partition if that has any influence on what I need to do.

Reboot using the Livecd and then use gparted to resize. It's found at "System > Administration"

---


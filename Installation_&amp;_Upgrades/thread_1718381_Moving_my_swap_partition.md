---
title: "Moving my swap partition?"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by RobotGymnast on 2011-03-31
I have two Ubuntu partitions, a side-effect of when I had Windows installed, installed Ubuntu, removed Windows, and installed Ubuntu into the free space. My partitions look like this:

/dev/sda1: My actual ext4 partition.
/dev/sda3: Extended partition.
/dev/sda5: Old Ubuntu partition, ext4 (can delete all this data).
/dev/sda6: Swap partition.

I'd like to remove /dev/sda3, /dev/sda5, and /dev/sda6, extend my /dev/sda1 partition to fill the entire hard drive (except 2 GBs), then create a /dev/sda2 swap partition to fill up my remaining space.

However, I don't know how to move my swap partition without messing things up, and I hesitate to try. How do I move my swap partition and get my system to recognize it?

---

### Post by Anonymous is Incognito on 2011-03-31
**Partitioning**

Make sure you switched swap off with the following command.

```
swapoff -a
```

Remove and create the partitions with

```
sudo cfdisk /dev/sda
```

or

```
gksudo gparted
```

Be sure to select swap as filetype for [FONT="Courier New"]/dev/sda2[/FONT].

**Utilising the swap partition**

[FONT="Courier New"]mkswap /dev/sda2[/FONT] will use the partition as swap space, but only for the current session.

To automatically mount the partition as swap on boot add the following lines to the [FONT="Courier New"]/etc/fstab[/FONT]:

```
/dev/sda2 swap swap defaults 0 0
```

Does this adequately answer your question?

---

### Post by RobotGymnast on 2011-03-31
Yes, that's great. Thanks.

---


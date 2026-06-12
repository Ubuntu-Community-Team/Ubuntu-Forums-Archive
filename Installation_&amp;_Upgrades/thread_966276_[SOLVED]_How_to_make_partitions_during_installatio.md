---
title: "[SOLVED] How to make partitions during installation"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Wiesje on 2008-11-01
Just bought an Acer Aspire One A150.
Since I got tired of Linpus (recovering over and over again) I thought Ubuntu might be a good idea.
Following the steps listed on [https://help.ubuntu.com/community/Aspir](https://help.ubuntu.com/community/Aspir) ... 07,2008%20)
I created an USB stick for installation from a 8.04 Live CD.
Takes some time (all night) but goes well.

Now I'm in the screen where I can prepare partitions. I've got no clue (yes, I'm a beginner to Linux!)
I've got 120Gb HD. I planned on creating a 20 GB Ubuntu-partion (enough?) 60 GB Data-partition and wat's left for backup etc.
Ok, I chose Manual partition. Looks like this:
/dev/sda
/dev/sda1 | ext2 | 118953 MB | 4600MB used
/dev/sda2 | swap | 1077 MB | 0MB used
/dev/sdb
/dev/sb1 | fat32 | 4108 MB | 719MB used

My questions:

   1. On wich partion do I create the partitions I want?
   2. When I chose edit partition, I have to chose Use as: (default 'do not use') what do I chose Ext2, Ext3, ...?
   3. And I have to chose a Mount point: (/, /boot, /home, /tmp, /usr, /var, /srv, /opt, /usr/local) Wich one to chose?

Thanks a lot for helping me out. Ifound a lot of related items, but nothing to answer these questions.

---

### Post by meindian523 on 2008-11-01
You create partitions on /dev/sda.Delete /dev/sda1 and create an extended partition.Within that 
1]create a 10-15 GB partition,use as ext3 and mount point /
2]60 GB partition,use as ext3 and mount point /home (this is your data partition) and 
3]rest as you wish for backup as you said,use as ext3/fat32/ntfs will do and mount point you can type as /backup

---

### Post by Wiesje on 2008-11-01
Great, thanks!
And the /dev/sdb, I leave it there like it is?

---

### Post by meindian523 on 2008-11-01
/dev/sdb is the USB stick you have plugged in.That's what you are installing from.

---

### Post by Wiesje on 2008-11-01
Ok *blush*. Sorry for the stupid question.

Thanks for your help!!!

---

### Post by meindian523 on 2008-11-01
Not stupid at all.The only way I could make out that /dev/sdb was the USB stick was by looking at it's size(4108 MB).

---

### Post by imbjr on 2008-11-01
> **meindian523 said:**
> Not stupid at all.The only way I could make out that /dev/sdb was the USB stick was by looking at it's size(4108 MB).

Though typically /dev/sdb is a USB device - but it's just not obvious.

---

### Post by meindian523 on 2008-11-01
imbjr,that's not necessary.It can be a second HDD too.In this case it wasn't,since OP mentioned only one 120 GB HDD.

---

### Post by Wiesje on 2008-11-01
Thanks a lot...

Now it says: "apt configuration problem" - "An attempt to configure apt to install additional packages from the CD failed" :confused:

---

### Post by meindian523 on 2008-11-01
Please create a new thread and explain what you were trying to do,and the exact error message you got.That said,the probable reason for that is that your Ubuntu CD is not in the drive.

---

### Post by imbjr on 2008-11-02
> **meindian523 said:**
> imbjr,that's not necessary.It can be a second HDD too.In this case it wasn't,since OP mentioned only one 120 GB HDD.

Interestingly under Ibex's LiveCD I saw two of my USB external drives listed as under /dev/sdc

---


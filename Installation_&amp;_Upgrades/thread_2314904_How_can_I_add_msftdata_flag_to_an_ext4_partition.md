---
title: "How can I add msftdata flag to an ext4 partition?"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by kschiff on 2016-02-24
[COLOR=#111111][FONT=Ubuntu]I have moved my partitions around to make room for dualboot, and now Windows 10 is on sda1 and sd2, with my linux install on sda3 (boot) and sda4 (home). I would like to access sda4 from my Windows install and am attempting to use Ex2Fsd in Windows. From what I understand, in order for this to work in Win10 I need to add the msftdata flag to my existing partition. I assumed I could do this in gparted, but there is no option for that. I installed gdisk, but don't know what commands to issue. I have a good backup of my partition.


[/FONT][/COLOR]

---

### Post by yancek on 2016-02-24
Are you sure the software you are trying to use, Ex2Fsd, will work on ext4?  Never used it myself so??  You might post a link to whatever site you are using for instructions and someone might see something you missed.  Manage flags is found by right clicking on the partition in GParted.  See the link below.  I'd do a little reading on this before doing anything.

 [http://www.linux.org/threads/gparted-partition-and-filesystem-flags.8112/](http://www.linux.org/threads/gparted-partition-and-filesystem-flags.8112/)

More details:

[http://www.rodsbooks.com/linux-fs-code/](http://www.rodsbooks.com/linux-fs-code/)

---

### Post by kschiff on 2016-02-24
Yes, the software should work with ext4. Apparently Windows 10 is finicky, hence the need to alter the flag. I did comment on a the Ext2FSD project page in reply to the user who had discovered the msftdata workaround.. no reply yet...

I'd seen the same article, but in my copy of gparted (and I tried this from latest live CD too) doesn't show the msftdata flag...

Here's what I see:

[IMG]http://i.imgur.com/ljcxNP0.png[/IMG]

---

### Post by kschiff on 2016-02-24
BTW, it appears that one can't manage this flags in gparted without an update/patched version of parted. Current version 2.3 doesn't allow for this.

---

### Post by sudodus on 2016-02-25
You can try this command to set the flag msftdata on /dev/sdx4. Replace **x** with **a** for /dev/sda4

```
sudo parted -s /dev/sdx set 4 msftdata on
```

I'm not sure if it works correctly with a Microsoft flag on an ext4 partition, but you have backed up your data, so it is worth trying. Good luck :-)

---

### Post by kschiff on 2016-02-25
Solution as follows:


1-run Gdisk from CLI
2-select disk (in my case it was /dev/sda)
3-select partition (in my case 4)
4-select "t" to change a partitions "type" code
5-enter "0700"

---


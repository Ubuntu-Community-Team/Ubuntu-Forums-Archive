---
title: "on harddrives and partitions"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by diskotek on 2007-09-22
i have a strange question (and poor english grammar) here. i have two physical harddrives 40 gb +  120  gb. 40 gb is master and 120 gb is secondary. i want to use whole 120 for my ubuntu. question goes here.. i did a fresh install on 120 gb but now it seems like booting slowly. it might be about being on secondary harddrive?  

master 40 gb harddrive is 30gb ntfs (windows xp) & 10gb ext3 (now empty), and 120 gb ext3 (ubuntu)...

what do you offer me?
should i make "/" directory on 10 gb (master) and "/home" directrory on 120gb? or do you think there won't be any change? and also this may cause any slowness..because of home directory and root directory are on different harddrive???

note: damn, i also can not understand what i wrote :confused:

---

### Post by pxwpxw on 2007-09-22
**diskotek**

How long is slow?
 
Unlikely to be caused by partitioning or 2nd drive, I get the same start up time for ubuntu on 1st and 2nd drive here (about 50 seconds).

More likely waiting for something like network startup, or file system check.

To see what is happening, 
in /boot/grub/menu.lst comment out "quiet" or "quiet splash"

Or to get a picture:
```

sudo aptitude install bootchart

```
(charts are in /var/log/bootchart)

---

### Post by diskotek on 2007-09-22
thank you for your reply, i just thought it was slow than my old box (which was bloated with programmes and well, tweaked for speed). after i moved my own "/hom" it became better. 

so  i think there is no difference first or secondary harddrives in this case. 

now i'll tweak it.. thanks :)

---


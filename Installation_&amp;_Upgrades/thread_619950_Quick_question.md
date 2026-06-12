---
title: "Quick question"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2007-11-22
I want to install Ubuntu on a specific drive on my computer. Does Ubuntu need it's own file system or would it be fine with NTFS? And, would an option ever come up during Ubuntu installation that would allow me to select which drive I can install it on?

Thanks!

---

### Post by aysiu on 2007-11-22
It needs its own filesystem. And, yes, the option will come up to allow you to select what drive to install on.

Read more here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by TV-VCR on 2007-11-22
Most of those are about installing Ubuntu on the same drive as Windows. In this scenario, Windows and Ubuntu have their very own dedicated drives (both are seagate barracuda SATA drives)

---

### Post by aysiu on 2007-11-22
> **TV-VCR said:**
> Most of those are about installing Ubuntu on the same drive as Windows. In this scenario, Windows and Ubuntu have their very own dedicated drives (both are seagate barracuda SATA drives)
Same principle applies, though. You can specify a separate partition or a separate physical hard drive.

---

### Post by TV-VCR on 2007-11-22
> **aysiu said:**
> Same principle applies, though. You can specify a separate partition or a separate physical hard drive.

Nice! As soon as Windows is done clearing out this drive I'll hop to installing ubuntu. :popcorn:

Thanks.

---

### Post by aysiu on 2007-11-22
Please make sure you have your data backed up. Even though the drive is a separate drive, there's always the tiny chance that you may accidentally select the wrong drive.

Caution is always best.

Ask lots of questions along the way, even if you think they're "stupid."

---

### Post by TV-VCR on 2007-11-22
Mkay. Well, The drive I'm going to install Ubuntu on is D:.

C: is windows, D: is blank, E: has a backup of windows but is otherwise blank.

So in the installation, would the target drive show up as D:? Or a different drive letter?

---

### Post by aysiu on 2007-11-22
See, that's the problem. The C:, D:, and E: designations are Windows only.

The Ubuntu installer will probably have them show up as something like /dev/sda1, /dev/sdb1, and /dev/sdc1, respectively. Or maybe /dev/hda1, /dev/hdb1, and /dev/hdc1.

---

### Post by TV-VCR on 2007-11-22
> **aysiu said:**
> See, that's the problem. The C:, D:, and E: designations are Windows only.

The Ubuntu installer will probably have them show up as something like /dev/sda1, /dev/sdb1, and /dev/sdc1, respectively. Or maybe /dev/hda1, /dev/hdb1, and /dev/hdc1.

Arrrgh... how can I tell which drive is which?

---

### Post by aysiu on 2007-11-22
> **TV-VCR said:**
> Arrrgh... how can I tell which drive is which?
Well, they tend to go in order (D: will probably be /dev/sdb1). There will also be a visual representation of the drives (I believe if they're separate drives, you may have to select which drive from the drop-down menu). You can also probably tell by the size of the drive in GBs.

To be safe, you might want to format the D: drive as FAT32 to set it apart.

---

### Post by TV-VCR on 2007-11-22
Ok, all has been successful so far.

I am at the partition menu. This is what it shows:
[IMG]http://img209.imageshack.us/img209/8600/screenshotlp4.png[/IMG]

Is the one that is highlighted the empty drive?

---

### Post by aysiu on 2007-11-22
That looks like the right one to me.

---


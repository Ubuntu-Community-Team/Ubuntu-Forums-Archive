---
title: "Kernel 2.6.20-15/16: yet another fsck error at bootime"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by qwerkus on 2007-10-02
Hi all,

As an ex-BSD lover (had to give it up because of the lack of hardware support), i'm not really fond of upgrades - but after more than half a year of good working, i decided to update my xubuntu laptop:
Wrong choice: it seems that i got some problem, passing from kernel 2.6.17 to 2.6.20.

The boot process hangs up at the fsck stage, here's the error message (may contain some typos):

```
* Checking file systems ...
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/hda1
/dev/hda1:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem, then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
      e2fsck -b 8193 <device>

fsck died with exit status 8


```

Before diggin into some risky partitioning operation, I would like to ask for some advice here: 
1. What's wrong with my dev/hda1 partition ?
2. Why don't this message show up when I boot 2.6.17 kernel ?

Thanks for your time,

qwerkus

---

### Post by qwerkus on 2007-10-03
Got it !  For some reason I do not understand fully, hda's are now called sda in my /dev path; so after a complete rework of my fstab file, it works now ...

---

### Post by Robynsveil on 2007-12-28
> **qwerkus said:**
> Got it !  For some reason I do not understand fully, hda's are now called sda in my /dev path; so after a complete rework of my fstab file, it works now ...
Hi, I noticed the same thing... quick question: did you replace the UUID numbers in your /etc/fstab file with just the /dev/sdax entry?
Also, are you dual-booting and if so, did you change the hdx to sdx for the NTFS drives?

---


---
title: "Where is the partition step?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by feeldead on 2008-10-30
Strange problem, I try to install 8.10 amd64 alternate version on Thinkpad x200 from harddisk. However, the step of setting up the partition is strange. 
The title of this step is something like "overview of the partition" There are 5 options to choose, something like:

1. help ???
2. <blank>
3. <blank>
4. undo all the changes
5. write to disk...

The 2nd and 3rd options are totally blank. It seems that the step of partitioning the disk is skipped. But the former step of this "overview" is "detecting the disk" So, where is the partition step?

I installed former ubuntu versions a lot of times. This is the first time I countered such wired situation.

Any suggestions?

---

### Post by Partyboi2 on 2008-10-30
did the iso md5sum match when you downloaded it? You should have got a partitioning stage.

---

### Post by feeldead on 2008-10-30
Yes, the iso, vmlinuz and initrd.gz are OK by md5sum checking.

---

### Post by Partyboi2 on 2008-10-30
Try checking the cd for defects, one of the options at the main menu, if there are errors then reburn at x4 or less. Sometimes there can be data corruption from burning to fast.

---

### Post by feeldead on 2008-10-30
I didn't burn the CD, but install directly from hard disk. And the alternate version don't have a option to check the CD. It seems that desktop has such a function only.

---

### Post by unutbu on 2008-10-30
You aren't allowed to repartition a hard drive while its partition(s) are mounted. Since you are running the installer from the hard drive itself, a partition on the hard drive must be mounted. This prevents it from being repartitioned.

I'm not familiar with installing ubuntu from a hard drive rather than a CD. There might be a way, but it will be more complicated than installing from a CD.

If you have the option of burning a CD, I'd highly recommend taking that route.

If not, here is a guide on other methods of installing ubuntu. Maybe one of these will help. [https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by feeldead on 2008-10-31
Oh, thanks very much. I'm so lazy that I only put "/vmlinuz" instead of 
"/vmlinuz root=/dev/ram ramdisk_size=1048576 rw" in the memu.lst. I will try again.

But I used the simple "/vmlinuz" days ago on a beta version of ubuntu. It works! Is that a bug of that beta version? Let me try.

---

### Post by feeldead on 2008-10-31
BAD, it doesn't work. I will try to install from USB.

---


---
title: "Installing Ubuntu 10.10 in a Seperate Partition"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Oloty on 2010-11-26
OK, So I Created a Separate Partition for Ubuntu using Windows. 

When I Try to Install Ubuntu Using the Live CD and I Choose the Partition I Made I get an Error Saying Something about no Root System.

What Should I Do?

---

### Post by oldfred on 2010-11-27
IF you use windows tools to edit windows partitions and Linux tools for linux partitions and you avoid issues.

If you are doing manual install you have to define / (root) and swap as the minimum required to install a system. The partitions have to be in Linux formats usually ext4 or ext3 not NTFS. Swap does not have a format.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by The Cog on 2010-11-27
Windows is not capable of creating the types of partitions that Linux needs. The easiest thing to do is to delete the partition where you wanted to put Ubuntu, and then install Ubuntu telling it to use the free disk space. The installer will create two partitions - one for the Linux system and one for use as virtual memory swap space.

Always ALWAYS back up your important stuff before repartitioning a system, just in case you make a mistake.

---

### Post by tt2000 on 2010-11-27
I found that the "install using free disk space" option is available in 10.04 but unavailable in 10.10. Is that correct?
Thanks.

---

### Post by Rubi1200 on 2010-11-27
> **tt2000 said:**
> I found that the "install using free disk space" option is available in 10.04 but unavailable in 10.10. Is that correct?
Thanks.
Yes, that option is no longer available in 10.10.

I recommend using the manual partition option, but be very careful!

For more discussions of the new installer:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by The Cog on 2010-11-27
> **Rubi1200 said:**
> Yes, that option is no longer available in 10.10.
Sorry, I didn't know they'd taken that option away. I wonder why they did that?

---

### Post by Rubi1200 on 2010-11-28
> **The Cog said:**
> Sorry, I didn't know they'd taken that option away. I wonder why they did that?
That is a very good question. For a more detailed description of some of the issues with the new Ubiquity installer on 10.10, I direct you to this thread posted by our friend kansasnoob:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---


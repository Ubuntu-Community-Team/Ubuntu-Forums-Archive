---
title: "Is it Possible to Use ‘Something Else’ to Resize Partitions?"
date: 2017-06-08
forum: Installation &amp; Upgrades
---

### Post by mew4 on 2017-06-08
I want to resize/shrink my root and home partitions to free up enough space at the end of my drive to install and dual boot Ubuntu. My current driver is Linux Lite. I&#8217;ve considered using Gparted but find it awkward at best and have read that applying a lot of changes in GParted can take a long time, in some cases a couple of hours or so. I don&#8217;t want to do a fresh install and resize my partitions that way because I want to keep my system&#8217;s customization. So the solution I'm going to ask about here might seem a bit crazy, but bear with me. I saw a video tutorial by Quidsup&#8203; called &#8216;How to use Partition Editor in Ubuntu Installer&#8217; -here&#8217;s the link:
[https://www.youtube.com/watch?v=OU_dkeFprhY]("https://www.youtube.com/watch?v=OU_dkeFprhY")

In this YouTube video, Quidsup re-installs Ubuntu, but more interestingly resizes his Windows ntfs partition but doesn't format it, so preserving it. So this got me thinking. To preserve an existing home partition (when doing a series install/upgrade in Linux Lite, for example) you would also leave the home partition unformatted to preserve it. So would it be possible to resize my root and home partitions using the &#8216;Something Else&#8217; manual installer in the live Linux Lite usb, but leave them both unformatted in order to preserve them, and then proceed to click &#8216;install&#8217; as required to complete the process (assigning grub to /dev/sda as normal). Would this destroy my OS, or instead preserve my customized OS with suitably resized partitions and new free space for my dual boot? Feedback please.

---

### Post by wildmanne39 on 2017-06-08
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by yancek on 2017-06-08
The time it takes to apply changes using GParted or any other partition manager depends entirely on the action being taken and I seriously doubt GParted takes any longer than any other partition manager.

You can use either a Linux Lite, Ubuntu or pretty much and Linux Live DVD/flash drive to shrink the partition to create unalloacted space for a new install of Ubuntu

---

### Post by oldos2er on 2017-06-10
Just be sure you have known good backups of your data before you proceed. Resizing partitions always carries a risk of data loss or corruption.

---

### Post by efflandt on 2017-06-11
Shrinking free space at the end of a partition is easy and quick. Moving the beginning of a partition or an entire partition are time consuming because "everything" in the partition has to be moved relative to the new location of beginning of the partition. If anything interrupts that before it completes (power failure, someone else turning off your computer, etc.) the partially completed partition move may make the partition unusable. So if moving the beginning of or entire partition you should preferably have uninterruptable power, and back up of anything you do not want to lose.

If you have Windows and want to resize its partition (typically to make room for Linux), that is best done with Windows' own Disk Management.

---


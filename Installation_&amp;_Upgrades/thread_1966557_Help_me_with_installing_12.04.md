---
title: "Help me with installing 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by FarGuddu on 2012-04-27
Hello, I'm new to Ubuntu. It's extremely difficult for a pure Windows user to play around with partitions and stuff. It's entirely different and sophisticated.

I have two partitions on my 500 GB disc.

One is 60 GB (had Windows 7 on it before) and the other very important partition is 405 GB with all my data on it which I can't afford to lose.

I'm trying to install Ubuntu, but the partition manager isn't allowing me to install it on the 60 GB partition. It says no root file system is defined. I can't erase the disc because I'm sure I'll lose all my data on the 405 GB partition.

I'm stuck here. Please, help!!!

---

### Post by nothingspecial on 2012-04-27
First off, I wouldn't go about installing a new operating system on your computer before you've backed up the important data you can't afford to lose.

When you get to the bit that asks you how you want to install Ubuntu, choose the option "Something Else"

Select the 60 gig partition and click "change"

Choose to use it as an "ext4 journaling file system"

Check/tick the format box

Select a mountpoint of /

Do not do anything with the other partition.

Once again, I really would back the data up first.

---

### Post by josim on 2012-04-28
I had this same issue.  Couldn't remember what I did with 10.10.:confused:  Joined this forum in order thank you for this response.:)

---


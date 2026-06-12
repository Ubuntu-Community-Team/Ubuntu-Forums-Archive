---
title: "Multi-boot Vista, Ubuntu + Kubuntu, partition &amp; common /home folder questions"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by PangoKen on 2008-02-11
Hi all,

I Have Vista installed on my desktop PC & would like to try and install both Ubuntu & Kubuntu on separate partitions so I can decide which flavour I like. I also have a couple of questions on the best way to manage the space on my HDD's and the files themselves. 

BTW: I have two hard drives, one 80Gb where the Vista OS is installed & a 500Gb which I've split into 2 partitions - one for my data + media files and the other for backup images. I've also got 4Gb RAM installed.

From reading various posts I understand that I should shrink the Vista volume to about 35Gb, create 3 more partitions: 1 for Ubuntu (20Gb), 1 for Kubuntu (20Gb) and 1 for the Linux swap (5Gb).

My questions are:
[LIST=1]
[*]Is this actually how I should set up the 80Gb OS disk?
[*]Will the Ubuntu and Kubuntu installations both be able to read the swap without any issues?
[*]Can I share my data & media files between all three OS's? How?
[*]Can I create backup images of the Ubuntu & Kubuntu installations and save them on the larger disk? (I'm using trueImage10 for Vista, what software is available for Linux?)
[*]What format should each of the partitions be?
[*]Is there anything I should be aware of (scared of!) when doing this?
[/LIST]

I'd appreciate any advice you can offer!

Thanks

---

### Post by otheracco on 2008-02-11
With this setup you're backing up onto one of the same discs that contains data.  If that disc crashes, you 'll lose everything except the OS's.  It's useless to have a backup on a separate partition of the same disc.

There are different ways to install a Linux distro.  It can be like Windows where everything is on the same partition, or it can be like UNIX where you have a different partition for /root, /home/, /usr, /var, and others.  

I think a good scheme for home installation would be to have a separate partition for /root and /home (and of course, /swap).

In your case, since your only evaluating the OS's, I would keep every mount point on a single partition, and then once you know which one you're going with, create a separate /root and /home.

I would back up your current Vista install onto that big disc before making any changes.  You should watch out for MBR problems, because you'll probably end up overwriting your Vista MBR.  GRUB should be able to boot into Vista as well as Ubuntu, but it's important to know how to edit the menu.list file in case GRUB doesn't automatically pick everything up.

---


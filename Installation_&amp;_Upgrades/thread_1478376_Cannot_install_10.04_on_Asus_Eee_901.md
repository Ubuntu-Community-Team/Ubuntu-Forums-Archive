---
title: "Cannot install 10.04 on Asus Eee 901"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by khanun on 2010-05-09
Tried half the day to install the Netbook version of 10.04 on my Asus Eee 10.04, but no.

I have not found any way of just running the installer, so I am in practice running it from the live environment. After answering all the initial questions (language, keyboard, account, etc), I am finally on what may be the core of my problem: The partition layout. Since this little PC arrived with a genuine POS version of Linux, I ditched both the installed version on the 16 GB drive **and** the restore partition on the 4GB drive, so in practice I have a 4 GB for administrative purposes and a full 16GB for the rest.

I select "Specify partitions manually" and move on. On the next screen I have tried keeping the layout that Eeebuntu used (that one worked) and I have tried deleting it all and then creating from scratch. The layout is:[INDENT]/dev/sda
  /dev/sda1 ext3 98 MB /boot
  /dev/sda5 swap 3931 MB
/dev/sdb
  dev/sdb ext3 16139 MB /
[/INDENT]Deleting all partitions on /dev/sda and then setting them up again works fine, doing the same on /dev/sdb results in "ubi-partman failed with exit code 141" as described in [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848) - except that I have an Internet connection up and running... But that is not really the main issue, a reformat will tak care of cleaning up anyway.

When I now push forward to install, it starts formatting and then it just sit there doing abolutely zilch.

I found a workaround: Do NOT format /dev/sda1 makes it display "removing conflicting operating system files" and then it goes on, but I can't say I like this idea. I think I'm going to do a manual sweep and then ANOTHER reinstall.

Any thoughts out there regarding my problem?

---


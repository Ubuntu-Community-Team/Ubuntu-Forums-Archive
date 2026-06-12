---
title: "Cannot (re)install Ubuntu 14.04 LTS"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by woosher on 2014-07-18
Hey Guys

first things first: I’m an absolute beginner with Ubuntu!! :-)
ok...

I wanted to use Ubuntu on my Desktop computer.
I downloaded Ubuntu 13.10 32bit, installed it, everything fine.

Unfortunately I really disliked the "Unity Desktop", that’s why I decided to install Kabuntu. I've tried Kabuntu within a Virtual PC and I really, really, really liked the KDE Desktop!!!

>> Unfortunately Kabuntu had a BIG graphic Problem on my Desktop PC... Nothing was displayed correctly.... Using Ubuntu everything looked normally.

Now I want to re-install Ubuntu 14.10 LTS, but every time I try my computer Displays the following error message: "general error mounting file system"

I’ve tried to delete all partitions in order to solve that problem: Failed.
After that I used the tool "boot repair disk“: Failed, too.

But now I've got this log file:
[http://paste.ubuntu.com/7814091/](http://paste.ubuntu.com/7814091/)


Anybody out there, who can help me?

---

### Post by ajgreeny on 2014-07-18
You definitely need to start again from scratch as there are no hard disk partitions showing in your boot-info report.

I recommend that you boot to the live DVD of whichever desktop version you want (I recommend Xubuntu as the easiest to use, but you may prefer Kubuntu) and using the live system start the partition manager gparted (may be just partitionmanager in kubuntu).  That should allow you to delete all the partitions that show, if any, and you can then start again.

I always use the "Something Else" option when installing as it gives more control, but it is not necessary to do so, and you should be able to choose to "Use whole disk" which will arrange partitions according to the disk size and ram available.

---

### Post by yancek on 2014-07-18
I haven't used Kubuntu 14.04 but, the last time I used Kubuntu there was no Something Else option.  It is still 'Manual' which is basically a different name for the same function.  There were two 'guided' options, either of which should work if you have an empty or unpartitioned drive.

---

### Post by ajgreeny on 2014-07-18
> **yancek said:**
> I haven't used Kubuntu 14.04 but, the last time I used Kubuntu there was no Something Else option.  It is still 'Manual' which is basically a different name for the same function.  There were two 'guided' options, either of which should work if you have an empty or unpartitioned drive.

Thanks for that.  I have never installed Kubuntu in my nine years of *ubuntu installs. I just assumed that Kubuntu used the same ubiquity as all the others, therefore assumed the manual partitioning was also called Something Else

---


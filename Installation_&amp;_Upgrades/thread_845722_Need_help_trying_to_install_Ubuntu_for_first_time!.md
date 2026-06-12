---
title: "Need help trying to install Ubuntu for first time!"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by mnemonik on 2008-06-30
First of all, I hope this is the right forum! And I thank you all in advance for any help that you can give me!

So I downloaded the ubuntu-8.04-desktop-i386.iso and the MD5sum hash check matched what it was supposed to. I used InfraRecorder to burn the iso to a disc, then I checked the integrity of the disc after boot up and there were no issues. I can run Ubuntu from the cd, however when I try to install I get stuck. I get through choosing a username and my keyboard and time perfectly and the problem comes about when I actually get to installing.

I use the guided partitioning and when the "installing system" window gets to the "partitions formatting" it freezes everytime at 5%. The task that it says underneath the status bar is "creating ext3 file system for / in partition #1 of IDE3 master..." I have tried this four or five times and it always freezes right there, I can't move the mouse or anything.

The computer is my Mom's Dell Dimension XPS T600r, and it was running xp sp2, however when I attempt to boot without the ubuntu installer cd it now says there is no OS.

What am I doing wrong??? Please help, and thank you to everyone who does!

---

### Post by bdalzell on 2008-06-30
Check out this HOWTO:
[http://www.funnestra.org/ubuntu/hardy/#install](http://www.funnestra.org/ubuntu/hardy/#install)

If you have no desire to have anything other than Ubuntu on this computer, when you get to the partitioning part of the install do the choice that allows manual partitioning.

Typically a linux install needs at least 3 partitions. Root ("/"), /home and swap.

I usually leave around 10% of the drive unpartitioned in case I want to do something additional with the drive later on.

---

### Post by tubasoldier on 2008-06-30
After you get Ubuntu installed you may find a load of answers at the [Ubuntu Guide]("http://www.ubuntuguide.org")

---

### Post by VMC on 2008-07-01
> **mnemonik said:**
> 
The computer is my Mom's Dell Dimension XPS T600r, and it was running xp sp2, however when I attempt to boot without the ubuntu installer cd it now says there is no OS.

I'm assuming that you want to keep mom's XP intact. So now we need to find it and find out what went wrong and where all the partitions are first. So boot the "LiveCD", and then go to "Applications-Accessories-Terminal" form within Terminal type the following. You can copy and paste it in the Terminal window or type by hand:

```
sudo fdisk -l
```

[That's a small or lowercase "L"]

Output the results back here.

---


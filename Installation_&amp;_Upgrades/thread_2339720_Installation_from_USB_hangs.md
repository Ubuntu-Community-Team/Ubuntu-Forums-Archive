---
title: "Installation from USB hangs"
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by Matt_Devney on 2016-10-12
Hi, I hope someone can point me in the right direction here. I've searched and none of the existing solutions apply to my situation (apparently).

I was running 12.04 LTS quite happily last year until I put the machine into storage (Dell Latitude D620 with 2 gb of RAM). Getting it out again this year it didn't like the number of updates required and Update Manager failed.

So, I thought I would just install 14.04 LTS over the top but the install isn't going past the screen where it states how much free space there should be and that you should be connected to the internet.

Tried installing from boot and installing from live CD (try before install option). Tried without internet and with internet. Tried with propriety software and without propriety software. Tried investigating partitions (mentioned in one solution) but don't really know what I should be seeing.

Which leads me to you guys. I hope you can help. Thanks in advance!

---

### Post by yancek on 2016-10-12
You don't need to be connected to the internet to install.  You can do the updates after installing.  Which installation type option are you selecting.  If you have not data you want to save, use the Erase disk and install option.  If you have data you want saved, is it on a separate /home or /data partition?  If so, just select the / (root) partition to install to.  You need the Something Else option to install which you don't seem to be using or you shouldn't be seeing that message about free space.

If this is an MBR rather than UEFI install, the tutorial at the link below is very detailed on installing 14.04.  Post back if you have particular questions.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---


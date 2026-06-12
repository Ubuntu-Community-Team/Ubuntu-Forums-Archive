---
title: "Installing Ubuntu 10.04 LTS Partition Problem/Win 7"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by AlexMason on 2010-07-17
I am having problems installing Ubuntu 10.04 it gets stuck at 4/8 of installing it shows no available partition's to use not even one's to right over windows 7.  I downloaded the 32-bit version could this be the problem?  Is the 64-bit version needed for Windows 7?

Thanks for the help this is a picture of my partitioned area:
[IMG]http://i27.tinypic.com/21e71i.png[/IMG]

---

### Post by viralmeme on 2010-07-17
> **AlexMason said:**
> it shows no available partition's to use not even one's to right over windows 7.
It looks like the harddrive is full, try and resize the C: partition using the Live CD and Qparted ..

Warning, fixing things that aren't broke can cause problems !

---

### Post by oldfred on 2010-07-17
I am not sure what N: is as a RAW format. If it is a partition then all four partitions are in use and you cannot install anything more without deleting one to make a extended partition that can hold additional logical partitions.

---

### Post by garnie on 2010-07-17
Try deleting the N: drive from the windows partition manager.
It should be able to see the free space then.

---

### Post by AlexMason on 2010-07-17
Thanks for the info ill try to get it working

---

### Post by AlexMason on 2010-07-17
This is the screenshot of installing error
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163761&stc=1&d=1279399519[/IMG]

---

### Post by AlexMason on 2010-07-19
bump

---

### Post by oldfred on 2010-07-19
Try running chkdsk on all the NTFS partitions.

I had trouble getting gparted to see my sda drive. My windows on the sda drive seemed to work ok, but after I ran chkdsk on the NTFS drive gparted did not have any trouble seeing my sda drive.

---

### Post by AlexMason on 2010-07-21
gparted sees my drives it just wont show up when installing PLEASE HELP I NEED THIS SOO BAD

---

### Post by oldfred on 2010-07-21
Try the alternate installer.

Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)


[https://help.ubuntu.com/10.04/installation-guide/](https://help.ubuntu.com/10.04/installation-guide/)

---

### Post by AlexMason on 2010-07-22
I fixed the problem my SATA drives had raid configuration left making them unsupported and not show up.

---


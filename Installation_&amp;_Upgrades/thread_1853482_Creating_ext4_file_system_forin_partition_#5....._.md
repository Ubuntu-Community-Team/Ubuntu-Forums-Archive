---
title: "Creating ext4 file system for/in partition #5..... stuck?"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by Film on 2011-10-02
Hello,

I recently installed Ubuntu 11.04 and everything went right untill I got to the partioning part were it got stuck saying:  Creating ext4 file system for/in partition #5...
I booted from CD and verified that it was working, I even tested Ubuntu first without installing and there were a few problems: I got no sound and no internet.

Now I had to shut the computer down because it wasn't doing anything anymore and now when I try again it created another partition which takes half my disk space away so I'm not letting ubuntu create another partition until the other one is gone.

Please help.

---

### Post by oldfred on 2011-10-02
Welcome to the forum.

If you want full control over sizes of partitions, you can use manual install. Then you choose partitions and formats, but have to specify which partition is / (root) and which is swap if new. If swap exists it auto finds it and you do not have to create another.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---


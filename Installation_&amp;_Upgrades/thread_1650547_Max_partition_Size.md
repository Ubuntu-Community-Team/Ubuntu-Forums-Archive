---
title: "Max partition Size"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Hiroka on 2010-12-21
The max partition size I can choose is 30GB, can anybody tell me how I can bypass this? Since I got 200GB on my hard disk and it will only allow me a max of 30GB to use at the installation...
Sorry if this has been posted before but I couldnt find anything with the search function so far.
 
Thanks in advance,
 
Hiroka

---

### Post by oldfred on 2010-12-21
Welcome to the forums.

You must be discussing wubi which has that limit.  Wubi is for those windows users to want to test Ubuntu without having to add partitions and possibly then just delete it. It is meant as an extended test over just using liveCD, but not for a long term install. 

You may be able to create /home separately, but I do not know wubi. If you want to give Ubuntu more space then just do a full install by creating partitions of whatever size you want to use.

This is just one suggestion:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

If you partition in advance you use manual install and choose the partitions for / (root), & /home if you have it. It finds swap automatically.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by Hiroka on 2010-12-22
Thanks for the reply, but could you send me a link to an ubuntu which has basically no max partition size while installing?
Since I already uninstalled Wubi and dont want to spend time to download it again.

Thanks in advance,

Hiroka

---

### Post by Megaptera on 2010-12-22
I think section 8 (Misc) paragraph 9 here refers to increasing size of Wubi install [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by Elfy on 2010-12-22
> **Hiroka said:**
> Thanks for the reply, but could you send me a link to an ubuntu which has basically no max partition size while installing?
Since I already uninstalled Wubi and dont want to spend time to download it again.

Thanks in advance,

Hiroka

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Hiroka on 2010-12-22
> **Megaptera said:**
> I think section 8 (Misc) paragraph 9 here refers to increasing size of Wubi install [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

Thanks, this will help me ;)
 
> **forestpiskie said:**
> [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
This is the 1 I installed but it still gives me only a max of 30GB, will use the tutorial above though ;)

---

### Post by Elfy on 2010-12-22
> **Hiroka said:**
> This is the 1 I installed but it still gives me only a max of 30GB, will use the tutorial above though ;)
Not if you download the real ubuntu and forget about wubi it won't ;)

Unless of course you don't have much free space on the drive anyway ...

---

### Post by dino99 on 2010-12-22
standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by psusi on 2010-12-22
Instead of clicking the wubi icon in windows, BOOT from the cd and install normally.

---

### Post by Hiroka on 2010-12-22
> **psusi said:**
> Instead of clicking the wubi icon in windows, BOOT from the cd and install normally.
 
Still comes up with max 30GB...
Btw I download it from ubuntu and run it, doesnt matter if I start on windows or boot from CD it just starts up wubi :s

---

### Post by psusi on 2010-12-22
> **Hiroka said:**
> Still comes up with max 30GB...
Btw I download it from ubuntu and run it, doesnt matter if I start on windows or boot from CD it just starts up wubi :s

No, if you boot from the cd you don't get wubi.

---

### Post by oldfred on 2010-12-22
Are you trying to install directly from windows? You need to create a liveCD or USB install disk.

If you look on this link already posted by forestpiskie it also has instructions on how to install.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---


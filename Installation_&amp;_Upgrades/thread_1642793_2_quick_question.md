---
title: "2 quick question"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by degarb on 2010-12-10
I have 3 hd + external drive on desktop gateway xp machine.  The 3 internal drives are all low on space.  The external has 153 megs free. 

1. If I install inside windows (you can boot to either), can I use ubuntu 10.1 if windows fails to boot?

2. Can I install (either inside or standard install) on external drive for something that will boot if something breaks in windows? 

3. Would boot loader choke if I: became another drive letter or another external drive added?

Okay, the third question is a bonus for me.

---

### Post by degarb on 2010-12-10
One ubuntu site for version 7 suggests unplugging internal drives during install to external drive.  This is insane, and probably outdated.  Too primitive for me.

---

### Post by dmp2010 on 2010-12-10
I thought you said two questions. And these are hard questions. You seems to be too concern about Windows breaking. Just leave it alone, use Ubuntu and Windows won't break.

---

### Post by oldfred on 2010-12-11
Did you mean 153GB free, if MB not enough room anyway.

wubi is for windows users to have an extended test of Ubuntu. But is not intended for long term use. It installs inside the NTFS partition (windows sees it as one large file), but works as a dual boot system using the windows boot loader.

If your windows breaks, you cannot use wubi to boot as you have to boot windows first, then it looks like a full Ubuntu boot but it is just loading like Ubuntu's full install. If NTFS gets corrupted, your wubi install also is in danger.

Boot loader does not care about how many systems you have installed. Many of us have multiple systems. I have 4 Ubuntus, XP & puppy on 3 drives. Plus two flash drives that I can boot if I plug them in.

The newest Maverick installer only lets you choose where to install grub2 the boot loader if you use manual install. Many are suggesting unplugging drives just to be safe. I never have, but always set partitions up in advance and use manual install. The grub2 installer likes to default to sda, so if installing to anything but sda you should use manual install.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---


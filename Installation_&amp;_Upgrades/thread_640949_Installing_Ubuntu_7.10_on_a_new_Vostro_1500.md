---
title: "Installing Ubuntu 7.10 on a new Vostro 1500"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by RogerMurdock on 2007-12-14
Hey guys, I looked at some similar threads to this one, but I couldn't find any straight up advice on my questions.  I'm getting a brand spanking new Vostro 1500 laptop in the few new days in the mail, and I was looking to possibly installing Ubuntu 7.10.  To put it simply: what is the best way to do this?  This would be my first linux installation ever.

I know the thing comes with a few different partitions already on there (I'm not sure if a windows recovery partition is there, but if so can I burn a windows cd from that?), and I would like to probably ditch those and put ubuntu on an extra 20gb partition. I also heard that something called "Media Direct" is installed, and will screw up Ubuntu if I press the buttons.  Can I disable these? Or at least can I keep ubuntu from getting messed up by them?  I know there are other problems (with sound and stuff), but I'm prepared to fix those or just let it be for awhile.  Plus I would like to do a fresh format of the Vista install as well, because frankly, I don't trust the pre-installed factory version.  Will my laptop come with a CD so I can do this?

I'm not exactly computer-retarded, but like I said this would be my first linux install and I'm trying to keep it as simple as possible.  I don't want to screw up and have to format the whole thing and reinstall everything again either.

Thanks for any help
-RogerMurdock

---

### Post by mikewhatever on 2007-12-14
There are lots of tutorials on how to install Ubuntu. Here are a few:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)

Basically, what you have to do is, resize one of the existing partitions (this will make some of the disk space unallocated), create root and swap partitions for Ubuntu in the unallocated space, and then install.

> I know the thing comes with a few different partitions already on there (I'm not sure if a windows recovery partition is there, but if so can I burn a windows cd from that?), and I would like to probably ditch those and put ubuntu on an extra 20gb partition.

That depends on the manufacturer. You should have asked them in advance.

> I also heard that something called "Media Direct" is installed, and will screw up Ubuntu if I press the buttons. Can I disable these? Or at least can I keep ubuntu from getting messed up by them? 

Media Direct is a striped down version of Windows for playing music and video. It simply sits on a separate partition, useless, but causing no harm to any other OS on the disk. Don't know where you got the idea Ubuntu would be messed up by it.

> I know there are other problems (with sound and stuff), but I'm prepared to fix those or just let it be for awhile. Plus I would like to do a fresh format of the Vista install as well, because frankly, I don't trust the pre-installed factory version. Will my laptop come with a CD so I can do this?

I don't know. Once again, it depends on the options provided.

---


---
title: "&quot;Creation of swap space.....failed"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by unklelar on 2007-06-28
At wit's end here. After a disastrous update yesterday which resulted in not being able to boot up, I'm trying to reinstall Ubuntu. I have tried to reinstall both 6.06 and 7.04. On the rare occasions I am able to get through to click the installation icon, I get error messages including, "file not found" and "The creation of swap space in partition #5 of IDE 1 master (hda) failed. 

Is there any way I can wipe my disk clean so I can reinstall Ubuntu? Otherwise, my whole system is compromised, and I can't recover it. So is my only alternative then to get a new hard drive to wipe whatever godawful problem was created?

Any help very much appreciated.

---

### Post by dabl on 2007-06-28
> **unklelar said:**
>  So is my only alternative then to get a new hard drive to wipe whatever godawful problem was created?

No, that's crazy-talk, unless your hard drive is actually the broken thing.  Let's assume for the moment it isn't, while bearing in mind we don't know that for certain ....

Setting aside my burning curiousity regarding what update happened yesterday, I recommend you download and burn the ISO to make a GParted live CD, from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Use that to view your hard drive, nuke the existing partitions (if that's what you want to do), make new partitions as you wish, set one of them to be bootable, etc.  I usually let the Ubuntu installer do the partition formatting, but GParted can do that too.

Then, I prefer the Alternate Install Live CD for (K)Ubuntu installation.  Follow the "guided installation" screens, and of course you do not need to do any partitioning with the Ubuntu installation CD because you already will have done it with GParted.  Just let it format and install filesystem mount points according to the way you set up the partitions in GParted, and you should be good to go.

:D

---

### Post by unklelar on 2007-06-28
Yep, I thought it was crazy too -- that is until I did a search of "grub won't load," "update problem," etc.and  read some other comments from other people about the same/similar thing happening to them.

I much appreciate your helpful suggestions and will try to find a way to follow through on them. Thanks again!

---

### Post by dabl on 2007-06-28
> **unklelar said:**
> Thanks again!

You're welcome.  One other late-breaking thought -- if you can verify that your Ubuntu Live CD is a good burn, and that your CD ROM drive isn't flaking out on you, those would be good things to be sure of.

;)

---

### Post by unklelar on 2007-06-28
Good burns, I'm sure. I've got 2 cys of 6.06 and 2 of 7.04 I ordered from Ubuntu. Problem is I can't download & burn the Gparted CD because my cd burner is on the amiss computer. Oh well. It's a Mac for me, I guess. Cheers.

---

### Post by dabl on 2007-06-28
> **unklelar said:**
> G I can't download & burn the Gparted CD because my cd burner is on the amiss computer. 

I see.  Well, if the amiss computer can boot and run the Ubuntu Feisty live CD, there is a version of GParted on it -- maybe that would suffice to nuke the hard disk and try again with partitioning, before attempting a Ubuntu installation.

---

### Post by unklelar on 2007-06-28
Yeah, dabl. I often only get a 'manual' option during installation asking me how I want to partition the disk. Exactly how do I specify a partition for the root file system (mount point "/" ? I'm also unable to get online for some odd unreason. Thanks.

---

### Post by unklelar on 2007-06-28
how do I run Gparted? Is that through the terminal? When I type it in, I get, "root privileges are required for running Gparted." Any way to get around this?

---

### Post by dabl on 2007-06-28
Ubuntu uses the "_S_uper _U_ser" theory of root user power.  So, to run a command as Super User, you preface the command with "sudo".  For example, ```
sudo fdisk
``` to run the fdsk command.  To run GUI applications with Super User privileges, however, instead of sudo you use "gksu", as in ```
gsku gparted
```

So, open your little console window, enter ```
gksu gparted
```, followed by whatever that password is that you use with the Live CD (it's been awhile for me) and you should be greeted with the GParted app ready to go to work for you.

BTW, do not fall victim to the common newbie notion that all kinds of problems can be solved by simply running your system as Super User for all mundane tasks -- that's a big mistake and you'll end up with a trashed system that is not fixable.

---


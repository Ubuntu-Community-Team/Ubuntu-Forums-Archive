---
title: "IRRITATING BUG:About the files getting corrupted constantly on ext3 by Ubuntu 7.04."
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by Odrodzona-Sarmacja on 2007-08-08
Ubuntu 7.04 corrupts its files on ext3 partitions constantly. I was suggested it is happening due usage of faulty older version of gparted during installation process of Ubuntu 7.04. The solution suppose to be to burn latest version of gparted livecd and check the ext3 partitions ubuntu 7.04 is on and correct whatever is to be corrected there with these Ubuntu 7.04's ext3 partitions.

However if something crashes Ubuntu 7.04's gdm (like when using wine), then you still get Ubuntu's files and libraries  on root "/" ext3 partition cuted by Ubuntu 7.04 system. I didn't see anyone posting so far any satisfying explanation why Ubuntu 7.04 constantly corrupts files on ext3 partitions and hates so blindly and furiously file downloading and even worser file torrenting. When torrenting it is smart to use preallocation, as Ubuntu 7.04 hates even more torrenting files, then the simple and strightforward file download from Ubuntu's repositories, which gives these problems with corrupted files on Ubuntu 7.04's ext3 partitions most often. It is even smarter to download files into fat32 partition instead of Ubuntu 7.04's extremly corrupting ext3 partitions. Sometimes it is better to be safe then sorry ;)

You can always try gparted lifecd. It is so far the only solution (partial solution at best if it works really) known to me for this problem, besides using fat32 extensively instead of that extremly faulty on Ubuntu 7.04 ext3 file system. Maybe it will help with files being corrupted on ext3 partion by Ubuntu 7.04 and maybe it will not be of much help. It would be helpfull if someone out there after couple of months of using Ubuntu 7.04 knew ways of fixing this irritating Ubuntu 7.04 os bug.

---

### Post by kidders on 2007-08-09
Hi there,

> **Odrodzona-Sarmacja said:**
> You can always try gparted lifecd. It is so far the only solution (partial solution at best if it works really) known to me for this problem, besides using fat32 extensively instead of that extremly faulty on Ubuntu 7.04 ext3 file system.I would very strongly advise against trying to run a Linux distro off a FAT32 filesystem ... it's simply not good enough, and would cause all kinds of odd behaviour. Ext3 on the other hand is among the most respected filesystems in the world. If you can identify the likely cause of your problems a little more precisely, I'm sure there's a good explanation for them. Personally, I've never heard of anyone having Ext3-specific problems on any operating system.

---

### Post by wpshooter on 2007-08-09
Perhaps, the posters hard drive is going north !!!

---

### Post by Odrodzona-Sarmacja on 2007-08-09
When I first meet that problem with file coruption on ext3 when using Xubuntu 7.04 it was unexplainable mystery for me, but when I did download quite few rars into ext3 partitions I found that every ten or so package was damaged and any try of deleting it from ext3 resulted in system crash (all files were locked into protected system files). This way I discovered _why_ these strange problems with Ubuntu 7.04 occure at all. None nowhere had even a hint about these errors done by Ubuntu 7.04 on ext3 partitions.

Corruption does occure only on ext3 file system. I run Xubuntu from ext3 partition. Xubuntu is corrupting files for me and other people, when we download files from internet... Most cases I noticed and something that did occure to me too is file corruption on ext3, when downloading files from Xubuntu repository servers.

However corruption also occure when Xubuntu/Ubuntu 7.04 also runs system. Temporary files can become corrupted or even sometimes system files of no appareant reason. Problems I had before running gparted lifecd were for example:

- programs close suddenly
- programs stop running
- programs give segmentation error when somebody tries to run them
- programs work only after reinstalation (sometimes also only after cleaning the setup files on /home directory)

I fixed that by checking ext3 partitions with latest gparted lifecd.

Now my left-over problems are that Xubuntu 7.04 is corrupting files (sometimes even system files) on all ext3 partitions, when i get system crash or shut the computer by switching power off. The problems left however are:

-programs close suddenly untill reinstalled

I didn't have much to test stability of file downloading on fixed ext3 partitions, because after d-bus security upgrade my Xubuntu doesn't want to start at all and freezes after giving me follwing errors:

[xx.xxxxx]Failed to execute /init
[xx.xxxxx]Kernel panic - not syncing: No init found. Try passing init = option to kernel

and I have now no clue how to fix that /init to make Xubutu 7.04 work again. Maybe I should copy that dir from somewhere... dunno from where yet.


Ext3 maybe is the best file system out there, but...
---**fsck sux!**---
Fsck destroys file system, when repairing it... it puts everything into lost&found directory. Now that's an idiot program and pity that if ext3 is so superior, then it uses the most dangerous recovery tool I ever heard about. I would trade fsck for scandisk for ext3 anytime if it was available. Futhermore Ubuntu 7.04, Kubuntu 7.04 and Xubuntu 7.04 corrupts frequently files on all ext3 partitions available for it. Maybe it is not fault of ext3, but sure like hell Xubuntu 7.04 NEVER corrupted a single file I was downloading into fat32 partition. **I'm sorry, but these are facts about ext3 file system on Ubuntu 7.04 linux. They are undeniable. I am not the only one having these file corruption problems on ext3, when using Ubuntu 7.04 os. They are common errors.**

If my hds were crashing, then I guess file corruption wouldn't be happening exclusively on ext3 partitions, when fat32 sitting besides works just fine.

---

### Post by kelvin spratt on 2007-08-09
well I never I've never had any of those problems and i constantly download from net. but then i don't run things like beryl as that could be causing this type of situation i suppose?.
i check all torrents for comments before downloading in the last 2 years i can't recall a bad one and i certainly don't get any corruption on my drives, its all formatted off  the alternate cd

---

### Post by Steveway on 2007-08-09
Sounds like your using ReiserFS and not ext3.
Reiser corrupted my files really often, too.
Ext3 on the other hand is rock-solid.

---

### Post by kidders on 2007-08-09
> **Odrodzona-Sarmacja said:**
> Fsck destroys file system, when repairing it... it puts everything into lost&found directory.This is a feature of fsck, not a *problem* with it lol.

Perhaps you could post some diagnostic information about your disk drives. It's difficult to offer help without any details at all about your system. You haven't even posted a partition table. :-(

---

### Post by merlinus on 2007-08-09
> 
[B]I'm sorry, but these are facts about ext3 file system on Ubuntu 7.04 linux. They are undeniable. I am not the only one having these file corruption problems on ext3, when using Ubuntu 7.04 os. They are common errors.
[/B]I can understand your frustration, but making blanket statements like these serve no purpose.

Facts? Undeniable? Common errors?  For you, yes, but have you done statistical research?

I cannot recall more than a handful of other instances reported on these forums relative to this issue, and I have not experienced these problems with any of my computers.

-merlin

---

### Post by vexorian on 2007-08-09
considering this is the first time I read about the issue, I wouldn't call these common or undeniable, heck I use 7.04 and ext3 all the time and it hasn't broke in a month...

Are you sure this is such issue and not the problem with hard disk flush on shut down?

---

### Post by kidders on 2007-08-09
I agree. In over a decade of Linux use, I have never heard of anything like this.

There are many people on this forum who are happy to help someone in difficulty, but making frankly ridiculous statements about ext3 and fsck is unlikely to encourage any of us to do so. Odrodzona-Sarmacja is obviously doing something he shouldn't be ... hopefully he can help us figure out what it is.

---

### Post by vexorian on 2007-08-09
I've been checking and it seems to be a problem with the kernel on some hardware:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)

My guess is that until the kernel devs fix it, it would be better to stay away of ext3 if and only if you experience the issues in your machine.

i have used this ubuntu install to download a handful of files, so I am sure that this is not something that happens on all hard drives

Edit: Moving to an older kernel might help.

Edit II: of course, using another fs should be good as well. Anyone knows of good ext3 replacements when formatting the partitions?

---

### Post by kidders on 2007-08-09
> **vexorian said:**
> I've been checking and it seems to be a problem with the kernel on some hardwareInteresting! Downgrading to a previous kernel version ought to fix it ... hopefully the issue hasn't been around long enough to force affected users to go too far back!

> **vexorian said:**
> Anyone knows of good ext3 replacements when formatting the partitions?All filesystems have their own unique features. (Ext3 is perhaps unique in its own way, in that it doesn't really have any lol.) I've used (or am using) ReiserFS, XFS & JFS without any difficulties, but I don't know if I'd use the word "replacement" to describe them hehe. My desktop box has JFS, ReiserFS and HFS+ on it at the moment. Anyone tried any others?

**Edit:** Wow! A lot of distros are reporting this problem. Looks like the guys at kernel.org made a booboo hehe.

---

### Post by louieb on 2007-08-09
> **wpshooter said:**
> Perhaps, the posters hard drive is going north !!!
Around here we call it going **south**. Anyway I agree that his hard drive is giving him a warning its about to die.

---

### Post by Odrodzona-Sarmacja on 2007-08-10
> **vexorian said:**
> I've been checking and it seems to be a problem with the kernel on some hardware:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)

My guess is that until the kernel devs fix it, it would be better to stay away of ext3 if and only if you experience the issues in your machine.

i have used this ubuntu install to download a handful of files, so I am sure that this is not something that happens on all hard drives

Edit: Moving to an older kernel might help.

Edit II: of course, using another fs should be good as well. Anyone knows of good ext3 replacements when formatting the partitions?

So, as I suspected it wasn't just only an issue of malfunctioning older version of gparted used in Xubuntu 7.04 installer. It is after all a composite issue, as I suspected all the time. **Thank you vexorian very much for the link&lead. I would never found that on my own.** Right now I am totally zeroed on what to do about linux, as these versions of kernel as I understand are not only something limited only to Ubuntu os, but more or less to all linux distros.

I think my problem is relatively old motherboard (over 5 years old now) as it gives me also some hardware conflicts with graphic accelerator too. It is not the harddrive, as I bought it just recently. I think the best solution will be for me just to buy a fresh new motherboard and then go over to linux for 100%. Then if I happen to buy motherboard giving these problems again... let's hope not.

Thank you vexorian very much again. Now at least I think how to proceed about that *file corruption on ext3 bug*. I really like linux even if so far the only distros I tested are Ubuntu 7.04 and Xubuntu 7.04. But they were certainly spectacularly superior to winxp imho and natural upgrades for win98. ;)

---

### Post by Odrodzona-Sarmacja on 2007-08-10
> **kidders said:**
> I agree. In over a decade of Linux use, I have never heard of anything like this.

There are many people on this forum who are happy to help someone in difficulty, but making frankly ridiculous statements about ext3 and fsck is unlikely to encourage any of us to do so. Odrodzona-Sarmacja is obviously doing something he shouldn't be ... hopefully he can help us figure out what it is.

The other day someone was asking for directory to which files from repository are being downloaded by synaptic and kept. He was asking because the file X.deb was corrupted during download. Only after removing the corrupted x.deb file he succeded in downloading it and then with instalation. It also seems to be common thema here in this forum from my observations.

edit: an example: [http://ubuntuforums.org/showthread.php?t=518949](http://ubuntuforums.org/showthread.php?t=518949)

Then on the other hand if 1%[sic! my guess] Ubuntu users writes here and then only 10%[my observation of posts here in forum] of them have exactly problems of this nature, then this issue is not something big generally, even if it is relatively common amongst others.

It seems problem of malfunctioning programs and downloads is of composite nature:
1. First part is something not working too well in older version of gparted which is used by Ubuntu 7.04 installer, so when manually partitioning all hell go loose causing all kinds of instalation problems. Using lifecd of latest gparted fixes problems on partitions caused by the older and less capable version.
2. Second part is an open offical bug with recent versions of kernels and the ext3 file system, which occures only on some computers. It is still an open bug, but it is official after all. My solution to this bug is to get more linux-compatible hardware and in my case it will be a new motherboard.

I think my statements were not ridiculous so far, but first hand observations. That "feature" of fsck, which destroys the file tree on harddrive and puts it into pieces in found&lost directory is some kind of bad joke. Fsck should be little smarter and not destroy the file tree, when fixing file structure on harddrive imho. Because of this "feature" of fsck I don't think anyone should even be using fsck untill this "feature" of fsck is totally fixed out of fsck. I even looked with google and then asked on forum for some replacement for fsck. There was none. So from my experience fat32 in this issue of repair&recovery is much more safe file system then ext3. In fat32 someone must type "format c:" instead of "scandisk c:", but "fsck" on ext3 is just a gamble. I have even warnings in Ubuntu against using fsck on root "/" harddrive without entire file system securily locked. However if some system file is bad, then I have no way really to fix it with fsck, have I. Anyway, for any hints about replacement for fsck I will be greatfull, as I intend to stick with linux in future ;)

---


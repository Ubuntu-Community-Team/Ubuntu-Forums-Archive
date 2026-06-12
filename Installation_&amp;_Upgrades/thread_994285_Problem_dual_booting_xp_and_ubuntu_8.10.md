---
title: "Problem dual booting xp and ubuntu 8.10"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by shoo56 on 2008-11-26
Hi

I am having trouble installing ubuntu 8.10 after installing xp on my laptop. The installation goes fine up until the end where the screen goes black and says:

Starting System Tools Backends system-tools-backends [OK]
Starting deferred execution scheduler atd [OK]
Starting periodic command scheduler crond [OK]
Enabling additional executable binary formats binfmt-support [OK]
Checking battery state... [OK]

The screen then goes black with a white cross like the one before the login screen and then goes back to the black one with the above writing again. After doing this a few times it remains on the screen with the writing.

I have installed this version of ubuntu on this laptop before with no problems and its only since installing xp that there has been this problem.

My laptop is an Acer aspire 5920

Thanks

---

### Post by emanresu on 2008-11-26
how did you set up your partitions? if you have the non-M$ OS on the 1st partition, you're gonna have problems until you put XP on the 1st partition.

---

### Post by shoo56 on 2008-11-26
At the moment I have not partitioned the hard disk so there is only XP installed on the entire hard disk. I am trying to use the ubuntu CD to resize the xp partition to half the size and create a new one for ubuntu

---

### Post by caljohnsmith on 2008-11-26
If you want to resize XP's partition, are you using Ubuntu's partition editor under System > Admin > Partition Editor? I would give that a shot if you aren't all ready using it. Let us know how it goes.

---

### Post by shoo56 on 2008-11-26
Still no good I'm afraid, I used the ubuntu partitioner to make the partition before installing this time and the same problem happened. The installation goes fine until after the '*Detecting Hardware*' part where it says '*Loading module sbp2 from firewire CDROM support*' or something along those lines - I didn't get to see it for long before I lost the GUI.

When I press the power button to shut down I get a message under '*Checking battery state [OK]*' that says '*Stopping gnome display manager*' - not sure if this is anything to do with it.

---

### Post by shoo56 on 2008-11-30
Anyone have any ideas? I've tried everything I can think of and it still won't work. I'm able to do the wubi install but would prefer to have it installed separately.

---

### Post by emanresu on 2008-12-01
shoo56,

i've completed a couple of dual-boot installs, but i'm not an expert, so i can't be sure how much help i can offer. 

do you have your Windoze restore disc(s)? you may need them.

when you had the partition set up, were you running the Ubuntu disc's partition manager as part of the install? or were you running from your computer's harddisk, already set up with Ubuntu? i ask, because the only method i'm familiar with is the 1st one.

i saw that you had Ubuntu installed 1st and are now adding XP. are you installing XP on the 1st partition? it needs to go first to have any chance at success. are you leaving enough space for the swap partition?

---

### Post by zimbot on 2008-12-01
you may wish to rePartition you xp partition w a win app like partition magic

---


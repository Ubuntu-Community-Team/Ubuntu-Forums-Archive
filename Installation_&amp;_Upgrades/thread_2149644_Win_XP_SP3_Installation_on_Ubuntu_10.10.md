---
title: "Win XP SP3 Installation on Ubuntu 10.10"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by fer493 on 2013-05-29
Hi fellow Ubuntu users!

I currently have a computer running Ubuntu 10.10 with the following partitions:

sda1 (/) ~ 7 GB total (3,1 GB free) - ext3
sda2 (swap) ~ 2 GB
sda3 (/home) ~  285 GB total (34,4 GB free) - ext3

Although I'm quite happy with Ubuntu, in spite of the fact that I can't seem to install any new software on it for some reason, I need to install Win XP SP3 over it in a dual boot in order to run proprietary software needed for work and school.

Given the above partitions comprise the total capacity of my HD, would you say there is a way to install Win XP over Ubuntu without losing my data and/or installed software?

Any help you could provide regarding my unability to install new software on Ubuntu would be greatly appreciated as well. The problem seems to be that any apt-get or Synaptic installation efforts end up showing a list of "404 - Source not found" errors due to which software cannot be retrieved, downloaded and installed. If a copy of the apt-get results would help, I can provide it as well.

Thank you in advance!
Greetings from Argentina!
Fer

---

### Post by oldos2er on 2013-05-29
10.10 hasn't been supported for over a year; its repositories have been moved to old-releases.

---

### Post by fer493 on 2013-05-29
> **oldos2er said:**
> 10.10 hasn't been supported for over a year; its repositories have been moved to old-releases.

I'm sorry but I'm not an Ubuntu expert. Does this mean there is not solution to my software installation issues other than upgrading my Ubuntu version?
Thanks!

---

### Post by ahallubuntu on 2013-05-29
~

---

### Post by ohnonot on 2013-05-29
it should still be possible to install software somehow. maybe you should check your software sources, from synaptic or /etc/apt/sources.list
but i would recommend to move your data and install a current LTS (long term support) version, maybe of the more lightweight xubuntu or lubuntu (lubuntu does not have an LTS version, but i still recommend the newest 13.04).

about win xp: it can run in  virtual machine on top of your linux, but if you want to install it straight to your machine, **you must install windows first and then linux!!!**
so, another reason to make a fresh start.

edit: someone beat me to it. also i see my **bold** advice was not entirely correct.

---

### Post by Mark Phelps on 2013-05-29
You will have to do three things:
1) Shrink the current partitions to make room for XP
2) Boot using the XP install CD and install it
3) Reboot using the Ubuntu LiveCD and restore GRUB to the MBR

For 1) and 3), you will need a LiveCD -- best to match the Ubuntu version you're using. You can download a legacy version from the following link:  [http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

For 1), boot using the LiveCD, choose Try Ubuntu and launch the Gnome Partition Editor (Gparted).  You might also have to unmount the swap partition by selecting that partition in the app window and choosing SwapOff.  Use this app to shrink the partitions to make some room for XP -- but do NOT create an XP partition.

After you have installed XP, your PC should boot directly into it.  To get GRUB back, follow the instructions in the link:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

And yes, you SHOULD upgrade to a newer version of Ubuntu -- but this should get XP on your PC for now.

---

### Post by fer493 on 2013-05-29
Thank you all for the detail and thorough responses!

It seems I'm not left with much options but to do a fresh install. If I do so, would the Win XP boot give me the option to create different partitions where to later install Ubuntu? 

On the other hand, I think I'll settle for Lubuntu given my computer is a bit old (AMD Athlon 64 Dual Core Processor 5200+ with 1,8 GB RAM). If there are any other lightweight Linux distros which are both fast and visually appealing, I'd appreciate your recommendations!

Thanks again!

---

### Post by ohnonot on 2013-05-30
> **fer493 said:**
> Thank you all for the detail and thorough responses!you're welcome!> It seems I'm not left with much options but to do a fresh install. If I do so, would the Win XP boot give me the option to create different partitions where to later install Ubuntu?yes! done that myself a few times.> On the other hand, I think I'll settle for Lubuntu given my computer is a bit old (AMD Athlon 64 Dual Core Processor 5200+ with 1,8 GB RAM). If there are any other lightweight Linux distros which are both fast and visually appealing, I'd appreciate your recommendations!that's nice to hear. if you're used to the feel of ubuntu 10.10 then xubuntu or lubuntu should do the trick. that said, there's many other stable, safe, minimalistic (and newbie-friendly) distros around. check out distrowatch.com!

i say it again, my advice earlier was technically wrong but probably still good advice for a layman (like myself).

---

### Post by fer493 on 2013-05-30
Thanks ohnonot and all for the responses! They're much appreciated :)
I'll try to do the fresh Win + Lubuntu install this weekend and if I experience any issues, you'll probably be hearing from me hehehe.

Best,
Fer

---

### Post by gordintoronto on 2013-05-30
You could also consider Xubuntu.

---


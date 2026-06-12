---
title: "Installation onto two hard drives"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by solidus23 on 2010-05-23
I would like to install ubuntu spanning mount points onto different hard drives(/ and swap on sda, /home on sdb). Though in ubuntu installation you can only choose one hard drive, sda. Is there a way to use both hard drives I have installed? I have double checked the connections and ubuntu recognizes the drive, yet wont allow me to use it for installation. Thanks.

---

### Post by darkod on 2010-05-23
For specifying /home partition you have to use manual partitioning anyway, it's not covered by the guided methods.
And manual partitioning should show you all disks and partitions in the list. So you should have no problems doing what you planned.
The second disk is not listed when you select manual partitioning?

PS. A disk used in raid which has raid metadata remains on it, will not show in the installer. To sort that out, boot into live mode first, and in terminal do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, depending)

If it asks you if you want to remove raid settings, that was your problem. Just remove them and the installer should work fine after that.

---

### Post by solidus23 on 2010-05-23
Yes even when inside manual partitioning, only sda is shown.

** EDIT**

Alright, thanks for your help, I'll try that out.

---

### Post by dabang on 2010-05-23
When the installer comes to point where you can manage the disk layout, did you try the "custom" option?? So far, this has always worked...

---

### Post by solidus23 on 2010-05-23
Alright I think that may have worked. Though I wanted to ask since someone might also know this. Is it possible to install Ubuntu onto an Intel SoftRAID? Everytime I setup a raid and run the ubuntu install, it breaks the softraid and I would have to re-create the raid. Thanks again.

---

### Post by darkod on 2010-05-23
> **solidus23 said:**
> Alright I think that may have worked. Though I wanted to ask since someone might also know this. Is it possible to install Ubuntu onto an Intel SoftRAID? Everytime I setup a raid and run the ubuntu install, it breaks the softraid and I would have to re-create the raid. Thanks again.

Not sure about that, but you probably know you need to use the alternate install cd for raid, right?
Also, if not planning to dual boot, actually the software raid feature of ubuntu is better to be used. You don't turn on raid in BIOS, instead you create identical partitions on the disks and ubuntu creates software raid.

These guides are a bit old, but to get you started:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by solidus23 on 2010-05-23
Alright, thanks again for all your help.

---


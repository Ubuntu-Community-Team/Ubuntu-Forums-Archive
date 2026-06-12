---
title: "New User: Ubuntu apprehension"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by JK0l1day on 2008-01-31
[FONT="Courier New"]How to RAID. Is Ubuntu unpolished when it comes to RAIDing? Each article has different methods. One solid standard promotes stability. Workarounds seem like a cheap quickfix.[/font]

---

### Post by chewearn on 2008-01-31
So, it there a real question in there somewhere, or are you just trolling?

---

### Post by JK0l1day on 2008-01-31
[FONT="Fixedsys"]Yeah I bought (two)HDDs coming tomorrow and was originally going to RAID on Windows until I started getting into Linux. I'm new to RAIDing and Ubuntu and was commenting on how there is a lack of a definitive guide on RAIDing in the Ubuntu environment.[/font]

---

### Post by chewearn on 2008-01-31
If you are asking that you need a tutorial on RAID, then ask:
"Can someone show me how to install a RAID set-up?  I have model X raid hardware, plus model Y harddisk."

---

### Post by yota on 2008-01-31
The simpliest way for a new user to get a Raid setup is to use the "alternate cd" which includes more advanced setup options.

To get it go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the "Check here if you need the alternate desktop CD" box.
During installation choose manual partitioning and setup your desidered layout setting "Linux Raid Autodetect" as partition type for the partitions that you'll use in an array.

If you want to explore the hard (and full featured) way you'll have to learn the "mdadm" command line tool (it's contained in the "mdadm" package available in the repositories).
In this case there's not a definitive tutorial since you can choose between a very large set of options and combinations: you have to learn the theory and design your own solution.
Anyway you can start at [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) (but beware, it's a bit outdated)

Have a look at this thread too: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Hope this helps.

---

### Post by polmir on 2008-01-31
Try this link:
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0")
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")

---


---
title: "Ubuntu/Xp"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by Faledask on 2007-10-14
I have three OS.
Ubuntu edu  Win Xp and Win Me
I have transfered everything that I want to keep off my Computer and I want to wipe me entire system leaving nothing but Bios. I only want to have Ubuntu and Xp. Would wiping my drives be the simplest thing to do?

---

### Post by Can+~ on 2007-10-14
I would use LiveCD, and use Gparted to format everything and them merge all into two partitions the size you like.

I don't know if there is a more practical and easy way.

---

### Post by Faledask on 2007-10-14
A co-work of mine suggested the same thing but then told me that I should install XP first. Can I install XP after installing Ubuntu and If I did would that make XP want to boot without giving me the option for Ubuntu?

---

### Post by oilchangeguy on 2007-10-14
> **Faledask said:**
> I have three OS.
Ubuntu edu  Win Xp and Win Me
I have transfered everything that I want to keep off my Computer and I want to wipe me entire system leaving nothing but Bios. I only want to have Ubuntu and Xp. Would wiping my drives be the simplest thing to do?

this may help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Faledask on 2007-10-14
Very much so thankyou. I have a coupple of bookmarks from that link now. 
: )

---

### Post by Can+~ on 2007-10-14
Windows XP usually tries to grab all the PC for itself, so, it's a safer bet to install Win XP and then Ubuntu. Last time I did the opposite, windows tried to "fix" it. So my process would be:

-Wipe the whole **** with the ubuntu LiveCD with gparted (or system rescue CD)
-Merge all in two partitions
-Reboot with XP disc, install in one of the partitions, finish.
-Reboot with ubuntu again, install in the other one.


Other way, if you want to have a full Linux system, and emulate windows:
-Wipe all and leave a big partition.
-Install ubuntu in the whole HDD.
-Download virtualbox and install windows inside. xD.

Good luck.

---


---
title: "I can't upgrade because my /home partition is formated in reiserFS. What to do?"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by Nesnej Trick on 2007-04-11
I've been wanting to upgrade from Dapper Drake to Feisty Fawn Beta for a while, but I can't because of a rather simple but stupid reason: my /home partition is formated in reiserFS, so Feisty would be unable to find it after an upgrade.

I wouldn't want to shell out some 55€ ($74 or £37) for a new HDD, but that seems to me like the only option considering that the contents of my /home folder weigh in at around 25,7 GB. I wouldn't really want to copy everything on DVDs either, because that would be slow and a complete waste of DVDs.

Any ideas on alternative solutions? Theis machine also runs Windows XP, but the windows disk has only 9,5 GB free space, so I can't back-up all the stuff there either.

---

### Post by Chowderpilot on 2007-04-11
Nesnej,

I am unaware of any way to retain the data on your Dapper partition since the file system is different from the default file system of ext3. My suggestion would be to backup your valuable files if you are going to try to upgrade. 

You will also need to upgrade to Edgy anyway before upgrading to Feisty, as noted in these upgrade instructions: 

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

Have a look at these if you haven't already, as it details how to upgrade. 

I hope this helps

--Dave

---

### Post by Nesnej Trick on 2007-04-11
I was under the impression that you can also do a normal "boot from disk"-installation.

---

### Post by Chowderpilot on 2007-04-11
Yes you can also do an install from CD if you prefer.

---

### Post by mpadams on 2007-04-11
Edgy & Feisty support ReiserFS: I've used it on both. I've also seen it as a selectable filesystem at install time. RedHat-based systems are ext3-only.

---


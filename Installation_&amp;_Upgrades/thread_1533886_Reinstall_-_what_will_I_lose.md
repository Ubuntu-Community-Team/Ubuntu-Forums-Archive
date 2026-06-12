---
title: "Reinstall - what will I lose?"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2010-07-18
I've been running Ubuntu since 7.04 on a server and the last upgrade to 10.04 worked, but then I started playing around with ebox - it completely hosed my system. 

I was running DNS and DHCP on the box as well as backups and a few other things.

I remember reading somewhere that an installation would only lose the things under your /home directory - which is fine by me.  Is that true?

If anyone can point me to documentation - I would greatly appreciate it.

Thanks is advance!

---

### Post by Old_Grey_Wolf on 2010-07-18
> **matthewboh said:**
> ...I remember reading somewhere that an installation would only lose the things under your /home directory - which is fine by me.  Is that true?

If you do a clean install then you lose all the changes you have made after installing 7.04. That includes data, preferences, software settings, and so on. Most of that stuff is stored in your /home directory by default. 

If you have a separate /home partition and select not to format that partition when you re-install the OS then you still have those; however, the newer versions of software may have difficulty working with the old files. The same thing happens with any OS, be it Linux, MAC OSX, Windows, etc. 

Best thing to do is backup you /home partition. :)

---


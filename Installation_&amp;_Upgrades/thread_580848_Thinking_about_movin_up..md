---
title: "Thinking about movin up."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by DOH on 2007-10-19
I am running feisty on a hp pavillion dv9000.  I tried to upgrade earlier today but it crashed.  I ended up just reinstalling feisty altogether. Can someone point me in the right direction of how to back up my system.

---

### Post by dilney on 2007-10-19
I suggest you create separate partitions for your system and your data.  Thus, you will have one partition mounted as the filesystem root "/" and the other as "/home".  This way, when you upgrade your Ubuntu, you'll save your data and personal settings.

However, you should also backup your /etc because the system settings are there.  If you didn't tweak your system a lot (apparently you just did a fresh install), I suggest you download a Gutsy CD or DVD and do a fresh install but partitioning the disk as described above.  Then, next time you upgrade you don't have to worry about your data.

Hope this helps.

---

### Post by DOH on 2007-10-19
I have a broadcom wireless card.  If i backup my info will the tweaks for this be backed up too?

---


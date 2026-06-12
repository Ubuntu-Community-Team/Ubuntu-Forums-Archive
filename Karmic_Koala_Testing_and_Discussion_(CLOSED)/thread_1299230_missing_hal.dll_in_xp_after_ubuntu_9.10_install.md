---
title: "missing hal.dll in xp after ubuntu 9.10 install"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by duruttye on 2009-10-23
Hey there, something messed up two systems in my house, and I can't figure out what...

So, here is what I have and what I did with it.

My girlfriend has a dell inspiron 1501. She told me, the open office was slowing down. No problem, I said, and installed ubuntu 9.10 without any problems. She has a separate /home partition, a partition for xp, and one for data storage. After all the configuration and the update, I wanted to start the xp, but in no avail..., it spilled out the missing or corrupted hal.dll file. Damn, I said, reinstalled the xp, searched all those stupid drivers, installed those, too, so, the XP was fine at that point. And guess what? After I reinstalled grub, (messed up the uuid...) I wanted to start the XP again, but to my surprise, here came the missing or corrupted hal.dll file. This was 2 days work, and, as you know, a real pain in the @ss...

I have a dell vostro 680, and it happened to my laptop, too, although I didn't start the xp in about 3 weeks, and I can't be sure that in my case it has something to do with ubuntu 9.10, or grub2, or something similar.

So, my question is: is out there somebody who may have the same issues? And maybe, just maybe, has somebody found a solution to this, or has some ideas?, 'cause every time my girlfriend or I need the XP (mainly statistics - spss) I won't be able to install the cursed xp all over again...

thank you all in advance!

---

### Post by GimmeCoffe on 2009-10-23
Did you install ubuntu on the same partition? If not, then ubuntu should not alter hal.dll...

~GimmeCoffe

---

### Post by GimmeCoffe on 2009-10-23
Check if you have hal.dll inside system32 folder.

~GimmeCoffe

---

### Post by duruttye on 2009-10-25
It is on a separate partition, and yes, it is there.
Somewhere I read, that this issue can be due to the boot.ini file being damaged, or something...

It is strange, that I have the same problem on both laptops...

---


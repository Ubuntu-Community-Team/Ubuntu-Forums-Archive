---
title: "[SOLVED] hardy firefox2 java problems solved"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by stumped on 2008-05-04
Running hardy heron and firefox 2.
I have installed and tried running java every way I could think of and it just wouldn't work. I looked everywhere on here without a fix.
On another web site I found this....

For java runtime env in firefox2 on 8.04 (Hardy) you need this symlink:

In terminal type:
cd /usr/lib/firefox/plugins

Then type:
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so


This solved my problem and now everything (even pogo) works great.
I just thought I would share this in case anybody else is having the same problem.

---

### Post by MrSnazzy on 2008-05-14
I love you.

---

### Post by finer recliner on 2008-05-16
worked for me too. thanks so much!

---

### Post by maxwellcom on 2008-05-17
Just the trick- thanks!

---

### Post by Ms_Angel_D on 2008-05-17
Thank You Soooooooooooooooooooooooooooooooooooo Much!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by stldirty on 2008-05-29
Yessssssssssssssss!!!!!!!!!!!!

---

### Post by Wartooth on 2008-05-31
You are a spectacular being.  Thank you, thank you, thank you.

---

### Post by Severian. on 2008-06-07
Thanks mate, worked like a charm! Firefox 3, good riddance!

---

### Post by eric1959 on 2008-07-07
I was looking for this answer, quick fix !

---

### Post by ashleycameron on 2008-07-07
Thank you mate... 
Your solution helped me..

---

### Post by RocketRanger on 2008-07-10
Sorry but which java version did you install?

I have tried both open java 6 and sun java 6 (jre for both) and neither has a plugin folder.

I'm running the 64bit version of Hardy.

Hope you can help.

---

### Post by jamesstansell on 2008-07-10
> **RocketRanger said:**
> Sorry but which java version did you install?

I have tried both open java 6 and sun java 6 (jre for both) and neither has a plugin folder.

I'm running the 64bit version of Hardy.

Hope you can help.

The openjdk6 plugin is in the icedtea-gcjwebplugin package.  There is no 64bit plugin for the sun-java6 JRE.

You may get more by looking at the sticky in the 64-bit users forum.

---

### Post by fatalbert on 2008-07-15
cool beans! I just spent the whole day with this.

---

### Post by Hachi-Roku on 2008-07-27
More props to you!

I wish i found this an hour ago. Ive been messing with all kinds of stuff to get this working, and in the end i was doing the right stuff in the wrong folder!!!! typical huh!

MODS....
It would be awesome if this java stuff was included in the hardy stater guide wiki. Or even a note/link saying its the same process as in the dapper wiki.

J

---

### Post by Macintosh SE on 2009-11-26
Worked for me! Now I don't have to go to my microscopic netbook to use Java apps.

---


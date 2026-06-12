---
title: "triple boot win7(or XP) + wubi 10.04 +wubi 12.04"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2012-08-26
Hi,
   I have been very happy with wubi 10.04 running alongside Windows (on two laptops running XP and 7, respectively). 

Before finally moving to wubi 12.04 I'd like to run my old 10.04 together with the new version by using triple boot (XP /wubi 10.04 / wubi 12.04) or - on the other laptop (WIn7/ wubi 10.04 / wubi 12.04). 

How can I do that? I see that the  wubildr and wubildr.mbr are different in the two versions and I am afraid that they have to match the respective version. 

I am also afraid that the procedure, if there is any, is different for XP and 7.

Thanks for hints, D-E

---

### Post by ajgreeny on 2012-08-26
I don't think you can have more than one wubi installation on the same windows OS, so you will probably need to think again.

---

### Post by Michi05 on 2012-09-02
I think that this may be what you want:

[http://askubuntu.com/questions/129149/how-to-enable-booting-multiple-ubuntu-wubi]("http://askubuntu.com/questions/129149/how-to-enable-booting-multiple-ubuntu-wubi")

At least is what I was looking for when I got here :)

Michi

---

### Post by dieter-erich on 2012-09-03
Hi Michi,
   thanks a lot for the hint! This is exactly what I was looking for! 

Sounds a bit risky, thouth, since I already once screwed up my system by fumbling in the grub files! So, have to backup everything first......
D-E

---


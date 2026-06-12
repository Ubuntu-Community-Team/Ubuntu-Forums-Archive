---
title: "dual boot on intel raid 0"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by smocco on 2010-03-04
Hello guys, here's my problem.

I set up an array of 2 hhd in raid0 using intel ICH7R, and i have a win7 installed on it. I'd like to have a dual boot with karmic, too. I googled a little bit and i found that it's not so easy as i thought. Are there anyone who's experiencing my same situation?
I'm really unexperienced in linux fake raid, and im sure that without any help i'll make a disaster :D

---

### Post by darkod on 2010-03-04
I haven't tried it but you have some info here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

In the Content there is procedure for the alternate cd, which should usually be used for raid, and for the standard desktop cd, which means it can be used too.

Otherwise, it doesn't sound too bad. Also, that guide mentiones 9.04, still not updated for 9.10 but the procedure would be the same. The only difference if using the live cd (not alternate) is that from 9.10 the package dmraid is already included I think, so no need to specifically install it.

---


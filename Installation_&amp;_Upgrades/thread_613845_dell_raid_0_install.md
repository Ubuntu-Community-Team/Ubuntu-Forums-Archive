---
title: "dell raid 0 install"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by emilemma on 2007-11-15
have dell xps410 with 2(250gb) hard drives configured as raid0, nvidia geforce 7950 graphics card, xp2 with sp2.
i have created a new ext3 partition on my "c" drive for linux.(25gb),  but when i try to install 7.04, it does not see the new partition and just displays the 2 physical hard drives for the install. am i doing something wrong, or is the raid0 config causing the problem? is there some way around this dilemma?

any help appreciated.

thanks
ee

---

### Post by Linuxxx on 2007-11-15
Ubuntu see the raid for what it is.. fake.. so you'll need to download a prgram called dmraid and some other stuff.. 

google raid 0 ubuntu and you will have a few guides to choose from.

Edit:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

---


---
title: "switch from i686 to amd64"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by [S2] on 2010-01-18
hi all.
when 8.04 came out, i installed the i686 kernel because amd64 support still wasn't that good. i still have that 8.04 install running (it is my mythtv htpc box), but when 10.04 comes out in a few months, i would like to upgrade ubuntu from 8.04 i686 to 10.04 amd64.
so my question: is a apt-get dist-upgrade from a i686 to a amd64 kernel possible? if so, how?

thanks!

---

### Post by audiomick on 2010-01-18
I don't think so, but don't know for sure. As far as I know, you have to re-install.

---

### Post by [S2] on 2010-01-18
> **audiomick said:**
> I don't think so, but don't know for sure. As far as I know, you have to re-install.

thanks for your answer, but i hope you are wrong, i have a lot of configuration done on that box, and re-doing everything would be a pain in the ***** :)

---

### Post by phillw on 2010-01-18
> **'[S2] said:**
> hi all.
when 8.04 came out, i installed the i686 kernel because amd64 support still wasn't that good. i still have that 8.04 install running (it is my mythtv htpc box), but when 10.04 comes out in a few months, i would like to upgrade ubuntu from 8.04 i686 to 10.04 amd64.
so my question: is a apt-get dist-upgrade from a i686 to a amd64 kernel possible? if so, how?

thanks!

Firstly, you'll need to get 8.04.4 when it comes out at the end of febuary, I'm not sure about how the 8.04.4 --> 10.04 update is going to happen, it may be worth popping your question onto the Lucid forum --> [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Regards,

Phill.

---

### Post by oldos2er on 2010-01-18
The only way to get 64-bit is to do a fresh install. Shouldn't be too painful if you have your home directory on its own partition.

---

### Post by audiomick on 2010-01-18
> **oldos2er said:**
> The only way to get 64-bit is to do a fresh install. Shouldn't be too painful if you have your home directory on its own partition.

if you haven't, found this today. It might interest you
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by [S2] on 2010-01-18
> **oldos2er said:**
> The only way to get 64-bit is to do a fresh install.

ok.

> **oldos2er said:**
> Shouldn't be too painful if you have your home directory on its own partition.

my home is not the problem. it's the mysql export/restore, reconfigure autofs, reconfigure lirc, reconfigure the imon lcd, reconfigure ... everything :)
but if it's the only way i'll have to do it. it's just once after 2 years.

---

### Post by oldos2er on 2010-01-18
You could make backup copies of your configuration files.

---


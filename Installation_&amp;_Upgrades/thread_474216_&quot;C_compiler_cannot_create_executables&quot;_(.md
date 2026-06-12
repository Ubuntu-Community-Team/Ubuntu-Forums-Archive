---
title: "&quot;C compiler cannot create executables&quot; (have not modified anything since reinstall)"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by maluze on 2007-06-14
Hi guys...I just did a clean install of Fiesty 2-3 days, ago, havent installed any programs (just Gstreamer plugins) since I reinstalled it. However, when i did try to install Pidgin 2.0.1, I get this message saying  "C compiler cannot create executables". Now i tried to find glibc in the ubuntu repositories (Synaptic), and its just not there...i could have swore i saw it there when i checked before..

what should i do???

---

### Post by avik on 2007-06-14
Install build-essential.

---

### Post by theharshone on 2007-06-16
I have this same problem except that i have installed build-essential but i still get that error. Why does this happen? BTW, i successfully compiled the latest nvidia beta drivers earlier today.
Could installing a package with weird depency have caused this?]

Thanks in advance

---

### Post by Rui Pais on 2007-06-26
> **theharshone said:**
> I have this same problem except that i have installed build-essential but i still get that error. Why does this happen? BTW, i successfully compiled the latest nvidia beta drivers earlier today.
Could installing a package with weird depency have caused this?]

Thanks in advance

Hi,
i found this question after i seen [another post of you on 64b section]("http://ubuntuforums.org/showthread.php?t=475623")... so i decided to reply to see if you have find an answer.

Do you added some personalization to cflags (at .bashrc or more globally)? 
Under 64 bits some flags fail with that warning (like -fno-idents...)

hth

---


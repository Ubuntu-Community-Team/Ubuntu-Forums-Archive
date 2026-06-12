---
title: "Can't install ubuntu in hp mini"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by msantamaria on 2011-01-29
I am trying to install ubuntu on hp mini , 10.10 version. When I try to boot form the cd the screen shows ubuntu logo but no progress from there, the screen still saying the same.  Anybody install it on a hp mini?

---

### Post by gordintoronto on 2011-01-29
Try Google. Thousands of people have installed on an HP Mini.

---

### Post by msantamaria on 2011-01-29
I guess that maybe on the official ubuntu forum someone can help me. I was wrong. 
I will check on google thanks

---

### Post by Quackers on 2011-01-29
A few things to check.
Check the downlaoded iso file md5sum
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok boot from the live cd again and at the first purple screen (with the man at the bottom, press any key then select language, then "check cd for errors".
If that's ok, at the same screen press the F6 key. This should bring up more options for boot parameters. The correct one will depend on some things, mostly graphics card. The nomodeset option is commonly used to get past this point, but as I say, your graphics card will decide which option(s) will work for you.

---


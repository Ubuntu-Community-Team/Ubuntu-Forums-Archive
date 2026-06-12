---
title: "Install CD of 10.04 won't boot properly"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by hvn on 2011-07-08
Hi,

The Lubuntu i.so had correct md5sum, and the burned CD (at 4 speed) shows correct md5sum as well. But when I want to boot from it, says "disk error 10, AX = 4200, driver EF". Tried in different systems where other CD's boot fine.
Can somebody tell me what's wrong ?

Thanks

---

### Post by Old_Grey_Wolf on 2011-07-08
I have never encountered this problem. I used Google to search for "disk error 10, AX = 4200, driver EF". It looks like you will need to burn the disk on another computer. You can use Google to search for "disk error 10, AX = 4200, driver EF" yourself to find the links that I found.

Hope you get the problem solved.

---

### Post by mörgæs on 2011-07-08
Have you tried booting from USB?

---

### Post by hvn on 2011-07-17
> **Old_Gray_Wolf said:**
> I have never encountered this problem. I used Google to search for "disk error 10, AX = 4200, driver EF". It looks like you will need to burn the disk on another computer. You can use Google to search for "disk error 10, AX = 4200, driver EF" yourself to find the links that I found.

Hope you get the problem solved.

Didn't find the exact error, but I burned the CD again. Boots fine now but hangs at some UID error. Still not clear why.

---

### Post by hvn on 2011-07-17
> **mörgæs said:**
> Have you tried booting from USB?

Unfortunately this pc is too old for having USB as boot option.

---

### Post by mörgæs on 2011-07-17
> **hvn said:**
> 
... hangs at some UID error. 
This is not much of a foundation for troubleshooting, People can only help you if you post the exact error message.

---

### Post by hvn on 2011-07-18
> **mörgæs said:**
> This is not much of a foundation for troubleshooting, People can only help you if you post the exact error message.

True. This is the message:

(process:215): GLib WARNING **: getpwuid_r(): failed due to unknown user id (0)

Thank you.

---

### Post by mörgæs on 2011-07-19
This thread explains;
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

You can jump to post 176, if you don't bother reading it all :-)

---

### Post by hvn on 2011-07-19
> **mörgæs said:**
> This thread explains;
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

You can jump to post 176, if you don't bother reading it all :-)

Thank you. That worked.

---


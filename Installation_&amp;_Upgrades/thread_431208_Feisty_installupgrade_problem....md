---
title: "Feisty install/upgrade problem..."
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by thetechgeek on 2007-05-02
Hey all,
I'm trying to upgrade to feisty and it is NOT working!
When i try to upgrade from update manager, it says it fails to fetch a file...
When i try to use a live cd, there is a graphics problem:
  -startup starts out with an average-looking command line underscore blinking.
  -then it goes to the screen where the ubuntu logo appears. I pick start or install ubuntu (oh, yeah, i already have edgy...)
  -then it goes to a black screen and prints a line of text.
  -then it goes black for like 2 minutes
  -then a stretched underscore appears bigger than the first underscore.
  -then it prints a couple of big, stretched lines of text.
  -then the screen goes black with the backlight off...
  -then the screen goes black with the backlight on...
  -then the computer just sits there, without the disc drive or hard drive working...

I REALLY want to upgrade to feisty!
I might have downloaded just the installer w/o the live cd...(dont think so, though...)
It might be a graphics problem, my computer is a dell inspiron 1100.

THX!!

UPDATE::
heres the error message i got when i tried to upgrade from edgy...-
```
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)

```

---

### Post by zvacet on 2007-05-03
You can replace your source list with this one,or just make your line like this

**[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main restricted universe multiverse**


[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")

---

### Post by thetechgeek on 2007-05-03
I have figured out that the problem might be the BIOS(?). Remember, this just-like an out-of-the-box 5-year-old computer. Also, would I need to use i910 or something? remember, the laptop BLACKS OUT doing absolutely nothing when booting from live cd(dont think update will work)! It also has multicolored static when going to edgy login (it dissappears then goes normal)

---

### Post by thetechgeek on 2007-05-04
Hey, great news-
i upgraded my bios from A06(omg!) to A22, and now feisty actually starts! i still don't see the neat new ubuntu loading screen with the loading bar, and i still see all the stretched text, but the system actually starts after the screen blacks out!
I KNOW that the problem is with the xorg.conf (whatever its called) file that a LOT of people have been having problems with. If you know EXACTLY how to fix this problem, please tell me.
Thanks,
Thetechgeek
(mabye ubuntu should just let you have the option of fixing the xorg file through a special editor...)
You can just point me to a person that had this problem, and i can go fix it myself (if you want to...):)

---


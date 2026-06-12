---
title: "upgraded to 10.10 RC, and software center crashed"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by khalid.A on 2010-09-30
Hi there all ubuntuians,
I just upgraded my ubuntu desktop edition from 10.04 to 10.10 RC, and everything went smoothly except the software center. When I try to open it, I got this message " Sorry, Ubuntu Software center closed unexpectedly." I've tried to reinstall it with no success. Any help to solve this bug would be appreciated.

---

### Post by mörgæs on 2010-10-01
This is a better forum:

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Goolie on 2010-10-02
It's not in it's final stages, so there can be a few kinks that need to be worked out.  Is it more of a hobby, I GOTTA see 10.10, if that's the case have at it.

But if you just need a reliable system, 10.04 is just perfect and doesn't really need upgrading.

---

### Post by khalid.A on 2010-10-10
Just in case someone has the same problem and wants to fix it.
I did this and everything works perfectly! 
```
sudo chown -R yourusername:yourusername .cache .config
```
This bug has been reported at [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/652151]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/652151")

---

### Post by fizmhd on 2011-03-15
> **khalid.A said:**
> Just in case someone has the same problem and wants to fix it.
I did this and everything works perfectly! 
```
sudo chown -R yourusername:yourusername .cache .config
```This bug has been reported at [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/652151](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/652151)


Thanks a lot This works 100% ...

---


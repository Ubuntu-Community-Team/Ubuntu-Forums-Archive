---
title: "how do i load and boot to an older kernal?"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by lilbluegremlin on 2008-06-22
i recently updated to hardy heron and everything seemed to installed fine.
however when i rebooted Ubuntu loaded and then froze to a black screen right before the login.
i was able to boot up using an old kernel 2.6.22-14 rather then 2.6.24-19 that is hardy.
want i have seen from looking around the forums is that 24-16 seems to work fine for plenty of people and i'm wondering how can i load an older kernel like 24-16?
or is there some other passable fix that i might use?
the old kernel is preventing me from loading the correct video drivers for my ati radeon x1950

---

### Post by lilbluegremlin on 2008-06-22
Just for a reference i followed this information and it fixed my not being able to boot into 24-19

> **Rocket2DMn said:**
> From safe mode, run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE or just reboot normally.
That will reset your xorg.conf file.  


---


---
title: "Can't load Live CD Ubuntu 12.04"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by blackalpinist on 2014-01-08
My computer crashes while trying to load kernel from LiveCD with message "unable to handle kernel paging request". I'd like to reproduce error output somewhere on forum to get some ideas on where to dig, but I can't figure out how to save that trace except by using photocamera. Is there some option to save output on hard drive, or at least allow scrolling to beginning of error. I have currently installed Windows and Ubuntu 9.10, trying to install Ubuntu 12.04. Same error happens with other Linux distributives. Thank you!

---

### Post by mörgæs on 2014-01-08
Hi, welcome to the fora.

In Ubuntu 9.10 please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---


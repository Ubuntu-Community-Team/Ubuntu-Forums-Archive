---
title: "invalid mit-magic-cookie-1 key"
date: 2018-10-10
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2018-10-10
I installed gparted on my new laptop I've upgraded 18.04. When I try to bring gparted up I get the error message invalid "mit-magic-cookie-1 key". My searching says this may have something to do with the Xauthority file. any help appreciated.

Larry

---

### Post by deadflowr on 2018-10-10
For clarity it's not trying to run wayland, what does
```
echo $XDG_SESSION_TYPE
```
show?

I would call that first things first, to get that possibility out of the way.

---

### Post by l6griffin on 2018-10-10
echo $XDG_SESSION_TYPE   =

x11

---

### Post by l6griffin on 2018-10-11
Seems I've had the problem about a year ago and got an answer here.

[https://ubuntuforums.org/showthread.php?t=2367174](https://ubuntuforums.org/showthread.php?t=2367174)

---


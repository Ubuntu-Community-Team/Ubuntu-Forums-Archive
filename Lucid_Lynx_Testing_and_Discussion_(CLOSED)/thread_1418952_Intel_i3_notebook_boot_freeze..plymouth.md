---
title: "Intel i3 notebook boot freeze..plymouth?"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by thonuz on 2010-03-01
Hi Folks,

I have had issues when I reboot my asus i3 will freeze at login screen every-time. No keyboard or mouse operable and no way to access another session, just complete lockup.

I removed plymouth and now I can log in every time. I don't know if this is the problem, but I am not going to reinstall plymouth until its fixed. Any ideas?

THanks!

---

### Post by pferraro on 2010-03-01
Are you using the on-die intel graphics or a discrete graphics card?

---

### Post by thonuz on 2010-03-01
Its intel on board. also my sony vaio with intel has same problem. So i am going to purge plymouth.

---

### Post by pferraro on 2010-03-01
I fixed my freezing problems on my i7 by upgrading to the latest intel xorg driver and drm from ppa:xorg-edgers/ppa
From the change log for :
[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)
"* Improved support for Intel® HD Graphics (in Intel® 2010 Core i7/i5/i3 Processor Series)."

---


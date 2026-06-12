---
title: "Fail on upgrade to 11.10"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Lord_ on 2011-10-20
Hi Everyone,

I have experienced a big problem on the upgrade from 11.04 to 11.10. Its basically left my system in an unusable state, without networking (eth0 and wlan0 have been removed from the /etc/network/interfaces) , and the hard disk was mounting as read only. If I try to boot normally, it will state waiting for disk mount, then wait for networking (for about 2 minutes) before finally stopping at a purple screen.

I can use Crtl + Alt + F1 to get a cli login, but many things are wrong.

I'm sure I can work through the problems to restore the system, but my main questions are:

1. Is there an easy way to re-install all the packages without a fresh install of the system?

2. If other people have had this problem, what steps did they use to resolve the issue?

Any advice welcome!

Thanks,
Joe

---

### Post by Sef on 2011-10-20
Reinstall the os would be the best choice.

---

### Post by Lord_ on 2011-10-20
From scratch on a wiped partition? Or can I use an install CD to detect and fix what I have already?



I think I can get most of my data backed up if I can mount usb or fix networking. It's my personal Laptop, so I can backup the home folder to preserve 90% of what I need.

Problem is everytime you do something like this you end up losing those things in kept in strange places, compiled programs etc ,etc.

---


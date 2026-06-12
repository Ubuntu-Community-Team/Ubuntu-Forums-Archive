---
title: "[SOLVED] Synaptic 'Reload' Corupt Messege"
date: 2008-11-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-11-15
When I click 'Reload' in Synaptic, it reloads then a messege box appears with the following messege
Any one know what it means or how to correct?
Thanks

---

### Post by ciscosurfer on 2008-11-15
Give it a shot: [http://ubuntuforums.org/showthread.php?t=653495](http://ubuntuforums.org/showthread.php?t=653495)

---

### Post by DougieFresh4U on 2008-11-15
Thanks for the reminder
dpkg --configure -a
I always run that when I am using terminal
This sound issue has got me doing all kinds of things I shouldn't be doing in 'Synaptic'
 I better leave it alone or 'bork' :lolflag:

---

### Post by dinxter on 2008-11-15
i seem to be getting the same error every so often, i have a funny feeling theres something going on with having the packagekit daemon running and synaptic but i cant seem to nail it down since it is happening only a handful of times in a hundred synaptic update attempts

---

### Post by MaX on 2008-11-17
> **dinxter said:**
> i seem to be getting the same error every so often, i have a funny feeling theres something going on with having the packagekit daemon running and synaptic but i cant seem to nail it down since it is happening only a handful of times in a hundred synaptic update attempts

Yes, this problem started appearing for me too when I installed Packagekit.

---

### Post by DougieFresh4U on 2008-11-17
> **dinxter said:**
> i seem to be getting the same error every so often, i have a funny feeling theres something going on with having the packagekit daemon running and synaptic but i cant seem to nail it down since it is happening only a handful of times in a hundred synaptic update attempts

> **MaX said:**
> Yes, this problem started appearing for me too when I installed Packagekit.

Well I have noticed that clicking on the 'update button' that it opens 'synaptic' and not the 'update manager'

---

### Post by dinxter on 2008-11-17
i'm assuming its both packagekit and apt accessing  /var/cache/apt/pkgcache.bin at the same time giving read/write problems and so flagging up a corrupt cache. both the packagekit applet and synaptic seem to be suffering the problem but i can seem to catch either when since it is not regular to get any bug information. i'll probably file a vague launchpad report soon if no-one else does if i cant generate any good info

---


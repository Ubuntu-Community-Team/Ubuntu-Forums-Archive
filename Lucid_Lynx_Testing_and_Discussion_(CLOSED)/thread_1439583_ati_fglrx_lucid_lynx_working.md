---
title: "ati fglrx lucid lynx working"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by farmercyst on 2010-03-26
i recently upgraded to lucid 10.04 and didn't realize that ati hasn't releases drivers for 10.04 yet! i found a solution to getting the fglrx driver to work. i have a hp tx2500 with hd3200 card. the solution was to install "fglrx" and "fglrx-amdccle" in synaptic. then by running sudo aticonfig --initial, and then sudo service gdm restart. 
look at post #29 and #43. [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699)

---

### Post by littlesatan on 2010-03-26
The main thread is here: [http://ubuntuforums.org/showthread.php?t=1434064](http://ubuntuforums.org/showthread.php?t=1434064)

---

### Post by farmercyst on 2010-03-26
> **littlesatan said:**
> The main thread is here: [http://ubuntuforums.org/showthread.php?t=1434064](http://ubuntuforums.org/showthread.php?t=1434064)

Thanks

---

### Post by ATOMICplayer on 2010-03-27
> **farmercyst said:**
> i recently upgraded to lucid 10.04 and didn't realize that ati hasn't releases drivers for 10.04 yet! i found a solution to getting the fglrx driver to work. i have a hp tx2500 with hd3200 card. the solution was to install "fglrx" and "fglrx-amdccle" in synaptic. then by running sudo aticonfig --initial, and then sudo service gdm restart. 
look at post #29 and #43. [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699)

Guys, Does this have to be done from a fresh install? Thanks.

---

### Post by waspbr on 2010-03-27
nope, it works with old installs as well, at least it did with my hd3300 IGP.

Just remember to do 

```
sudo aticonfig --initial
```

after you install it

---

### Post by Yfrwlf on 2010-04-01
Worked, thanks.  Graphics card fan speed now being throttled properly, otherwise I'd have stuck with the open source ATI drivers.

I'd recommend doing a reboot though instead of running gdm restart from your desktop, it just caused my computer to freeze on a black screen, and I had to run aticonfig again and reboot a 2nd time afterwards before it kicked in.  fglrx doesn't use kernel mode setting, so it's not surprising I guess that you can no longer switch between virtual KMS-driven terminals after installing it.

---

### Post by libihero on 2010-04-01
random question probably stupid...
does this include the legacy cards also?

---

### Post by djchandler on 2010-04-01
Yeah, it works after the hoop jumping, which hopefully will be fixed soon. But I'm getting a corrupted boot splash screen now with the latest kernel and Plymouth updates.

I have an AMD 780V chipset in my laptop with HD 3100 IGP.

---


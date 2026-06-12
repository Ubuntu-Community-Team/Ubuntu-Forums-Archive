---
title: "A few problems and questions"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by ToleDragoon on 2007-10-31
I have tried installing the previous version of Ubuntu, but it didn't work, as when I came to step fo selecting my hard drive, it didn't show any.

I guess there wasn't a driver for my hard drive (If anyone knows what the problem really is, please post) , as I have a fairly new pc, so I waited for 7.10 to come out and I have ordered a cd, and I hope I will be able to install it. Does anybody know where I can see what kind of of hard drive I have?

I have another important question, if I get Ubuntu installed, I really need my printer to work.
Does someone know if there exists a driver for the "HP Color Laserjet 2820"?

P.S.: I hope you can understand me. English is not my native language.

---

### Post by taurus on 2007-10-31
If you can boot your machine with one of the LiveCD (order release or newer release, doesn't matter), open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by ToleDragoon on 2007-10-31
Wow, that was a fast response. :) Thank you 

That's for checking what Hard Drive I have? I shall try it.

The next step will be finding a driver for it, and a way to get it installed 
(Is it possible to burn a new disc with the driver included?)

---

### Post by taurus on 2007-10-31
Let's just take one step at a time.  Will see what happens with the output first, okay.

---

### Post by ToleDragoon on 2007-10-31
I understand

I'm on my Live Cd now. I've typed the command in the terminal and it just gives this
```
ubuntu@ubuntu:~$ 

```

The standard line that also appears when I just press enter.

---


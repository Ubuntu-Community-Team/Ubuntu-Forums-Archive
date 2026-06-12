---
title: "The Lynx ate my Fox!"
date: 2009-12-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by trulan on 2009-12-28
Whenever I try to start firefox in Lucid, I get this:
```
trulan@ubuntu:~$ firefox

(firefox:4634): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault
```It's been this way for a few days, I thought maybe another update would fix it but so far no joy.  Tried reinstalling firefox, that didn't help either.

That's the problem with putting a carnivore in charge of your OS. ;)

---

### Post by plun on 2009-12-28
Can you start in safe mode ?

```
firefox -safe-mode
```

Start clean first without any check box ticking....

---

### Post by jerrylamos on 2009-12-28
> **trulan said:**
> Whenever I try to start firefox in Lucid, I get this:
```
trulan@ubuntu:~$ firefox

(firefox:4634): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault
```It's been this way for a few days, I thought maybe another update would fix it but so far no joy.  Tried reinstalling firefox, that didn't help either.

That's the problem with putting a carnivore in charge of your OS. ;)

I get that complaint too, but it does go on to start.  

With gnome desktop, firefox running O.K.  With LXDE desktop selected, firefox doesn't do youtube flash, something about javascript??

Jerry

---

### Post by ronacc on 2009-12-28
getting that also here on amd64 , getting it in -safe-mode too but it does start either way and seems to work normaly.

---

### Post by fluteflute on 2009-12-28
I was getting that on startup on the Koala today, but it's gone now.

---

### Post by trulan on 2009-12-29
Apparently the first complaint is normal then.

Apparently the segfault is not normal.

If I start in safe mode, I get the little window with the check boxes.  No matter what I select, it will flash a bigger window, then die with the segmentation fault.  It's on AMD64.  It behaves this way on the NVIDIA drivers or on the vesa drivers.

I purged all the firefox related stuff I saw in synaptic, rebooted, and reinstalled.  I'm still getting the same thing.  Obviously something is broken and I'd like to find it.  I'll keep looking...

---

### Post by ronacc on 2009-12-29
look at the depends for FF and see if maybe you have got one of them that is not the default .Just a guess .

---


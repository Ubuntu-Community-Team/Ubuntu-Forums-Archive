---
title: "Lubuntu... horrid problem"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by hellrazor236 on 2010-05-05
I installed Lubuntu 10.04 yesterday (yay, my first serious installation!), and I was trying to install the drivers for my video card (GeForce 6200),  when it told me that it couldn't use **ld**. After oing some research I found out that it was in binutils. So I went over and got it and tried to **./configure** it when it told me that there weren't any C compilers in **$PATH**,
so I went over to the gcc homepage with a fine-toothed comb and found gcc 4.5.0. When I tried to**./configure** it, it also told me that there aren't any C compilers in **$PATH**.

I'll admit I'm decently new to Linux (I know a few commands, 'bout it), I'm just wondering what I should do.

---

### Post by wandalalakers on 2010-05-05
I have the same problem with Kubuntu and a Nvidia 7300se.
I'm just going to wait and hope this problem will be fixed the next .1 release.  I'm running everything ok except my favorite opengl screensavers.

---

### Post by cariboo on 2010-05-05
You shouldn't have to, but make sure you have build-essential installed, it is in the repositories.

---

### Post by phillw on 2010-05-05
Hi, in order for me to able to compile stuff up (specifically pcmanfm during testing), I put these onto my lubuntu system.

[http://wiki.lxde.org/en/PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/PCManFM_build_and_setup_guide)

Regards,

Phill.

---

### Post by hellrazor236 on 2010-05-06
Will try!

---


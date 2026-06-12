---
title: "help a newcomer - new kernel"
date: 2018-02-12
forum: Installation &amp; Upgrades
---

### Post by desezar on 2018-02-12
hello im all new to ubunto - and want to learn -- someone said i should upgrade  from 4.10 x   to a 4.13.x kernel.  can anyone help me with that?

thanx a bunch!

---

### Post by kc1di on 2018-02-12
Hello desezar and welcome to Ubuntu,
one of the easiest ways to upgrade kernels is to us a tool called ukuu you can learn about it [here ]("https://itsfoss.com/upgrade-linux-kernel-ubuntu/")
It's not the best way but for those new to ubuntu it's the easiest. 
good luck. 
P.S. please read the warning on that page and follow it's advise before upgrading the kernel.

---

### Post by Impavidus on 2018-02-12
If you have the proper kernel packages and metapackages installed, that upgrade from kernel 4.10 to 4.13 should have happened pretty much automatically along with your other normal updates. No need to do anything special.

When in doubt, show output of this:```
uname -r
lsb_release -d
dpkg -l | grep linux-
```

---

### Post by gordintoronto on 2018-02-12
If you are using the 4.10 kernel, I think that means you are running Ubuntu (or one of the family members) 17.04, which is no longer supported. You need to do a dist-upgrade to 17.10.

But first, you make sure you have good backup!

I recently did this with Xubuntu, and it went very smoothly. First, I backed up my /home folder to another computer on my network, and also to a large flash drive.

---


---
title: "Burg doesn't update with new kernels"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by setherd on 2010-02-21
I noticed tonight I was still running 2.6.32-12 when I had just installed 2.6.32-14 earlier today.

turns out burg isn't updating it's self when  new kernel is installed. a simple "sudo update-burg" solved it.
I seem to recall burg used to have some link that when update grub was done it also did update-burg.
am I the only one with this issue?

---

### Post by dino99 on 2010-02-22
hm, not tested burg yet, is it bringing some usefull features ?

---

### Post by setherd on 2010-02-22
> **dino99 said:**
> hm, not tested burg yet, is it bringing some usefull features ?

easy nice grub theming
[http://ubuntuforums.org/showthread.php?t=1371288&highlight=burg](http://ubuntuforums.org/showthread.php?t=1371288&highlight=burg)
I really like it.

---

### Post by andrewthomas on 2010-03-08
> **setherd said:**
> I noticed tonight I was still running 2.6.32-12 when I had just installed 2.6.32-14 earlier today.

turns out burg isn't updating it's self when  new kernel is installed. a simple "sudo update-burg" solved it.
I seem to recall burg used to have some link that when update grub was done it also did update-burg.
am I the only one with this issue?


This should help.

[http://ubuntuforums.org/showpost.php?p=8780157&postcount=216](http://ubuntuforums.org/showpost.php?p=8780157&postcount=216)

---

### Post by setherd on 2010-03-08
hmmm sounds like a good idea, I'll try it!

---

### Post by bean123 on 2010-03-09
The configure file is /etc/kernel-img.conf. You just need to change update-grub to update-burg and it'd be run automatically.

---


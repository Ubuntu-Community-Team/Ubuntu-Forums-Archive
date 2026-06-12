---
title: "No hard drives detected on install"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by yelserpdog on 2006-12-18
x

---

### Post by scrooge_74 on 2006-12-18
When you boot the live CD does it recognize your drives?

---

### Post by yelserpdog on 2006-12-18
Just had to go back in to chck and No, it doesn't detect my hard drive from the live cd

---

### Post by scrooge_74 on 2006-12-18
Is your bios recognicing your drive? Set it to automatic to see if it detecs it

---

### Post by yelserpdog on 2006-12-18
Yes, the Bios detects it (it's one of the options when I choose to boot from the cd). It's the laptop I use all the time.

---

### Post by scrooge_74 on 2006-12-18
> **yelserpdog said:**
> Yes, the Bios detects it (it's one of the options when I choose to boot from the cd). It's the laptop I use all the time.

That is weird, post the details of your laptop, maybe someone else had a similar problem. give all the details you can even brand and model

Edit: I read back your post and saw the brand name, try using a Dapper CD and check if there is an ISO for AMD 64 in particular

---

### Post by taurus on 2006-12-18
From the LiveCD,

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by yelserpdog on 2006-12-18
Shoul I keep in this thread?? If so

It's a Dell Inspiron 1501, it's about 1 month old, AMD Turion 64 processor, 512mb ram, 80 gig hard drive. Everything's woking fine on WIndows XP, no problems.

---

### Post by redDEADresolve on 2007-01-02
use the info in this thread:

[http://ubuntuforums.org/showthread.php?p=1782230#post1782230](http://ubuntuforums.org/showthread.php?p=1782230#post1782230)

I recommend using the pci=nomsi

not only do you need to add it to the liveCD boot
once installed you need to add it agian
and also edit your /boot/grub/menu.lst file

place pci=nomsi in the kernel line at the end

---


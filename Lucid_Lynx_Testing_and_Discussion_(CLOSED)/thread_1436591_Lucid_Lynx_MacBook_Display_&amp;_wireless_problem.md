---
title: "Lucid Lynx MacBook Display &amp; wireless problem"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sunha1007 on 2010-03-22
I installed ubuntu 10.04 beta on my black book.

For some reasons, my display doesn't work properly.

After logging in i can see my desktop for about a second then it goes to black.

I tried reinstalling broken packages but the problem is still there. 

And My wireless network doesn't work either.

I edited /etc/network/interfaces to set up my wlan with static IP.

At first, it kept connecting and disconnecting over and over by itself.

Then, it's gone forever.

Does anyone has the same problem with Macbook's display and Atheros wireless?

---

### Post by CCBalla10 on 2010-03-23
I haven't had this problem at all.  But I am using the 13" aluminum uni-body macbook.  When I 1st installed 10.04 I installed all the updates on the 1st boot.  Then when I restarted I install the restricted drivers when I saw the pop up thing by my clock stating their were hardware drivers for me to download.  Been running perfectly after installing those 2 drivers.  Wireless works (as well as telling me how strong my signal is) and I have the correct screen resolution.  Maybe try wiping Ubuntu and re-installing?

---

### Post by cybik on 2010-03-24
Edit the grub boot entry and, on the kernel line (it starts with "linux", put "i915.modeset=0"). Small hack to get it working.

I'm still working on getting GrubEFI to work. New version seems to have a mind of its own and is stubbornly resisting any sane attempt at making it work.

---

### Post by mnml on 2010-03-28
I have the same issue, I have to boot and use xterm windows manager instead of gnome.
I have tried to edit the /boot/grub/menu.lst but the file doesn't exist, how can add the entry?

---

### Post by waspbr on 2010-03-28
menu.lst is the config file of grub 1, the current version of grub is 2. and the name of the file is grub.cfg , more precisely:

```
/boot/grub/grub.cfg
```

---

### Post by mnml on 2010-03-28
thanks a lot that worked

---


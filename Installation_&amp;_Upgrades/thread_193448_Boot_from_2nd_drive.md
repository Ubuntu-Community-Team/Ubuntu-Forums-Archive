---
title: "Boot from 2nd drive"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Drakkor on 2006-06-10
I was wondering if I could install Ubuntu on the 2nd drive and still have it dual boot with XP? Thanks :-k

---

### Post by aysiu on 2006-06-10
Yes, if you install Grub to the MBR, which you can specify on the Alternate Install CD, and which is the default behavior on the Desktop CD.

---

### Post by Drakkor on 2006-06-10
Thanks for the reply so fast,aysiu, I downloaded the Ubuntu Desktop-i386.iso,
will that work the same??

---

### Post by aysiu on 2006-06-10
Well, that won't ask where you want to install Grub--it'll just install it straight to the MBR, which is what you generally want (there are odd situations where people want to install Grub to a particular partition or to a floppy disk).

---

### Post by Drakkor on 2006-06-10
Ok, I'm going to give a go,and see what happens. I will post back on what happens.
Thanks :)

---

### Post by aysiu on 2006-06-10
Before you give it a try, just take a look at this first... oh, and back up your files, just in case!

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---


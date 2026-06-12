---
title: "I think there is a memory leak."
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-03-27
Got 780 meg in use with only compiz and firefox running.

---

### Post by ghindo on 2009-03-27
How long has Firefox been running?  What is Firefox running?  Any Flash videos?  Are you sure there aren't more services running in the background?  Have you checked top/htop?

---

### Post by philinux on 2009-03-27
> **ghindo said:**
> How long has Firefox been running?  What is Firefox running?  Any Flash videos?  Are you sure there aren't more services running in the background?  Have you checked top/htop?

1 hour, no flash, checked top. Only rebooted an hour ago.

---

### Post by zevans on 2009-03-27
Yep, mine seems to have got more and more swappy with every update, and yesterday I ran out of swap - never happened before.

When I ran out of swap I assumed it was VirtualBox, imagine my surprise when konqueror was using MORE vm than VirtualBox was!

I probably had used Flash at some time during that session - why, is there a known problem with it?

---

### Post by rage-against-windows on 2009-03-27
I had firefox using 499mb's last night testing Jaunty, and Nautilus was using up about 200+. After a huge update this morning all went back to normal, thank god! Something was for sure not right LOL.

---

### Post by Chemical Imbalance on 2009-03-27
Latest firefox for me is using 312mb right now with just one tab and no flash opened.  Fairly normal for firefox I guess.

---

### Post by jotavrj on 2009-03-27
:P

I'm waiting Jaunty anxiously! Only a month!

---

### Post by Chemical Imbalance on 2009-03-27
> **jotavrj said:**
> :P

I'm waiting Jaunty anxiously! Only a month!

How bout give the beta a test run?

[http://mirrors.gigenet.com/ubuntu/9.04/](http://mirrors.gigenet.com/ubuntu/9.04/)

---

### Post by zevans on 2009-03-27
I just remembered, mySQL lite had a memory leak that appeared and was fixed again in some of the latest kernels - perhaps that's it.

---


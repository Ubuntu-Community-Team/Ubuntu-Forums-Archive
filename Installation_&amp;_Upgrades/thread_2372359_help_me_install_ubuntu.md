---
title: "help me install ubuntu"
date: 2017-09-24
forum: Installation &amp; Upgrades
---

### Post by satoshi1nakomoto on 2017-09-24
hello all, I am new to linux and installing ubuntu.

I am at installation type
I see /dev/sda
Free space
/dev/sda1 fat32 536mb
/dev/sda2 ext4 991gb
/dev/sda3 swap 8.5gb

I want my disk d from windows to be saved.

What should I do ? Thank you

---

### Post by kc1di on 2017-09-24
> **satoshi1nakomoto said:**
> hello all, I am new to linux and installing ubuntu.

I am at installation type
I see /dev/sda
Free space
/dev/sda1 fat32 536mb
/dev/sda2 ext4 991gb
/dev/sda3 swap 8.5gb

I want my disk d from windows to be saved.

What should I do ? Thank you

Hello satoshi1nakomoto  and Welcome to Ubuntu Forums,

According to the partions listed above you do not have a windows partition to save. the fat 32 partition is a boot partition. 
If you wrote what you have above to disk already your windows partition was over written.
if you haven't hit install yet you can go back to the partition page and recover the windows partition or partions and shrink the one you want to use for Ubuntu and select install along side windows.

---

### Post by satoshi1nakomoto on 2017-09-24
So my disk d is deleted ? What should I do now ...

I was at final stage with one install setup than I force shutdown and bere I am

---

### Post by jigitup on 2017-09-24
You could be a bit more specific in terms of partitions, perhaps a screenshot; On the other hand, I do not clearly understand the question. Do you want to install Ubuntu next to Windows? Do you want to configure partitions manually?


- Sorry for my English.
- Original language: Spanish;
- Translated with Google Translate :'v

---

### Post by satoshi1nakomoto on 2017-09-24
I started installing ubuntu with erase disk and at last step I shutdown.
So I guess data was deleted.
Now I need to restore data and try to reinstall

---

### Post by yancek on 2017-09-24
The Erase disk option has a warning line below it which states that it will "delete all programs on any operating systems" and that's exactly what it does.  You might be able to recover some data using software such as test disk but I doubt you will get much.  You can try booting the Ubuntu install media and downloading test disk from the link below and running it by I would not expect much.  There is a link with Step By Step instructions on that page.  


[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by kc1di on 2017-09-24
If you desire to dual boot the machine you should use the install ubuntu along side of Windows option. 
[Here is a page ]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")that will help you when you reinstall. 
There are other available but I find this one quite easy to follow.

---


---
title: "Jaunty, ext4, netbook -&gt; grub error 15"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by billgoldberg on 2009-04-13
I just installed Jaunty on my Eeepc and after install I got a nice grub error 15, which means that grub can't find something.

I booted into the live cd, and installed grub again 

(sudo grub, find xxxgrub, root (hd1,0), setup (hd1) and succeeded in installing grub)

but it still gives the same error.

---

### Post by taavikko on 2009-04-13
Grub error 15:
> 15 : "Error while parsing number"
 This error is returned if GRUB was expecting to read a numbur and encountered bad data.

So, try installing latest kernel again, so it will build initframs and runs update-grub.

---

### Post by uidb4056 on 2009-04-13
How many disks you have? and how many partitions on them? can you post from live cd the result of fdisk -l (lower case L)?

---

### Post by billgoldberg on 2009-04-13
> **taavikko said:**
> Grub error 15:


So, try installing latest kernel again, so it will build initframs and runs update-grub.

Will do so, hope it didn't have to come to that.

:p

---

### Post by sahabcse on 2009-04-13
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by billgoldberg on 2009-04-13
> **uidb4056 said:**
> How many disks you have? and how many partitions on them? can you post from live cd the result of fdisk -l (lower case L)?

Two ssd drives.

The first one is just one big fat32 drive (/dev/sda) , the second one has ext4 / (dev/sdb1) and swap (/dev/sdb5).

---

### Post by billgoldberg on 2009-04-13
> **sahabcse said:**
> For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

Dude, while I appreciate the help you are trying to offer, if you read my OP, you'll see that I already done this (a few times) and it doesn't work.

---

### Post by billgoldberg on 2009-04-13
I just hoped there was an easy fix, I guess not.

Reinstalling will be faster.

Grub can be a mess sometimes.

---

### Post by Sef on 2009-04-13
Moved to Jaunty.

---


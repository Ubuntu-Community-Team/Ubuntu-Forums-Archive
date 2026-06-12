---
title: "Dual Boot Ubuntu 16.04 Install (Thinkpad Yoga) - Please Help"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by tommyguntragedy on 2016-08-21
Hello,

I have a Lenovo ThinkPad Yoga 12 on which I am trying to perform a dual boot install of Ubuntu 16.04

I have a 256 GB SSD on my Yoga and by default it had three partitions

[ATTACH=CONFIG]270797[/ATTACH]

I allocated the ~40GB to perform the install.  Once I booted to Ubuntu Install from USB, I proceeded to select the free space to create a "swap drive" of size 16GB.  After creating the swap drive, the remaining memory became "unusable" and I could not go back in to grab and create the root for install based off the following youtube video:

[https://www.youtube.com/watch?v=SOfnvbdWhrs](https://www.youtube.com/watch?v=SOfnvbdWhrs)

I think the reason the rest of the allocated memory became "unusable" has to do with the four partition limit.

Does anyone know how I can fix this to proceed with dual boot installation?  A class for school is requiring the ubuntu which is the reason I am doing this.

Thanks,
tommyguntragedy

---

### Post by Impavidus on 2016-08-21
Make sure you create the swap partition and Ubuntu's root partition as logical partitions. In that case you'll have a so-called extended partition as you fourth primary partition, acting as a container for all logical partitions you need.

16GB swap space seems excessive. Making your swap twice as large as your ram was good back when you only had 1 GB of ram. The only case where you want more than 2GB of swap is when you hibernate, but you are so limited on hard drive space that I wouldn't recommend it.

---

### Post by tommyguntragedy on 2016-08-22
Impavidus thank you so much.  I will attempt this when I get home from school today.  What size do you recommend making the swap drive?  I have 8GB of RAM, that's why I thought I needed 16GB of swap drive space.  

So I can perform the process (@ 5:25 -  [https://www.youtube.com/watch?v=SOfnvbdWhrs](https://www.youtube.com/watch?v=SOfnvbdWhrs)) that I see in that youtube video but instead of choosing "primary" choose "logical" for both the swap drive and the root?

---

### Post by Impavidus on 2016-08-22
Yes, choose logical instead of primary at that point in the video.

I'd recommend about 2 GB of swap space. With 8 GB of ram you'll probably never need swap and you can install Ubuntu without a swap partition, but having some swap space is useful. If you run out of memory (unlikely with 8 GB of it), swap space will slow the computer down, so you know what's happening and can quickly close some programs. Without swap, random programs will crash when you run out of memory.

If you want to use hibernate, you need swap space at least as large as ram. Pay attention to the difference between GB and GiB, with 8 GiB ram you need 8.6 GB swap space to hibernate. But you have a relatively small hard drive and Ubuntu boots quite fast, so I recommend you don't use hibernate.

---

### Post by tommyguntragedy on 2016-08-22
Impavidus,

I am pleased to be typing this response to you from Ubuntu OS.  Everything worked perfect when i did the installation the way you told me.  I made the swap drive 2GB and made both partitions logical.  Went flawless.  Thank you so much for your help!!!

---

### Post by Impavidus on 2016-08-22
Splendid.

Could you mark this thread as solved? Click thread tools (near top of page) -> mark as solved.

---

### Post by tommyguntragedy on 2016-08-22
Done.  Thank you again!

---


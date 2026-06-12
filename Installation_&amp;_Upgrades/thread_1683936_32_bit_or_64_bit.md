---
title: "32 bit or 64 bit?"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2011-02-08
I have read the Sticky on the Pros and Cons on whether to use the 64 bit version of Ubuntu over the 32 bit.  Only thing, it was dated on 2007.  Here we are 4 years later, is there any improvement with or less Cons in using 64 bit Ubuntu?  I am getting ready to replace my Ubuntu 10.04 32 bit with the 64 bit.

---

### Post by dino99 on 2011-02-08
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by Slim Odds on 2011-02-08
> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

That's a pretty poor explanation....

I've been using 64 bit for a long time and see no reason not to use it on a machine like the OP.

The main reason that the sticky is outdated is because there aren't so many issues with 64 bit these days.

---

### Post by cascade9 on 2011-02-08
@ Slim Odds- agreed. Unless you've got some odd hardware with 32bit only drivers (very rare) then you might aswell use 64bit IMO. 

> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

Blog post is dumb right now- 

> PAE ( a sort of intel-esque duct-tape hack to add additional bits to a 32 bit arch ) has been implemented in most modern CPUs. This means that we can up the old RAM cap of 4294967296 bits. PAE lets you address more RAM without going all the way to 64 bit mode.  PAE can also be extended up to 52 bits to address around 4-5 petabytes ( 4.50359963 × 10^15 ).


No mention of the 3/4GB limit per process that PAE has. So yeah, you can run huge RAM with PAE, but no single process can use more than 3/4GB (depending on the version) 

> So, 64 bit users, do you have more then 5 petabytes of RAM? If not, why are you using 64 bit arches? 

Becasue 64bit is faster in general, and a hell of a lot faster for audio/video encoding.  

Stick that in your petabyte pipe :P

---

### Post by garyjmellor on 2011-02-08
I've used 64-bit Ubuntu (currently 10.10 Maverick) longer than I did 32-bit. I've got no problems with it and it's always been reliable. I've got a pimped Lenovo G550 with 8GB RAM, Nvidia graphics, a 120GB SSD and an Intel Core2 Extreme Processor. Everything works straight out of the box as it were, including wifi. I'd recommend 64-bit for sure.

---

### Post by Vorian Grey on 2011-02-08
I've used both and I prefer 32 bit.

---

### Post by oldfred on 2011-02-08
I switched to 64bit several versions ago, and cannot say I have any issues related to 64 bit.

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.

---

### Post by gilloz on 2011-02-09
Thanks everyone for your replies. I removed, re-formatted the partitions and installed the 64 bit version of Ubuntu 10.04.1.  So far, as I am configuring it to my liking, it is working just fine.  Thanks again for your support.

---


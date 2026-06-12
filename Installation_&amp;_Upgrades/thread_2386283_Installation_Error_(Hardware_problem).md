---
title: "Installation Error (Hardware problem?)"
date: 2018-03-03
forum: Installation &amp; Upgrades
---

### Post by torm on 2018-03-03
This is my machine:

[https://www.amazon.com/VivoBook-E203NA-YS02-Featherweight-Dual-Core-processor/dp/B076BFSMPV/ref=sr_1_3?ie=UTF8&qid=1520082800&sr=8-3&keywords=asus+e203na](https://www.amazon.com/VivoBook-E203NA-YS02-Featherweight-Dual-Core-processor/dp/B076BFSMPV/ref=sr_1_3?ie=UTF8&qid=1520082800&sr=8-3&keywords=asus+e203na)

and I'm trying to install Xubuntu 16.04 LTS from a USB I created with Etcher. I booted to the USB, chose install from the boot menu, and it stops with this error:

[https://ibb.co/jz8mHn](https://ibb.co/jz8mHn)

The computer works fine otherwise, and I've been able to use the Live boot of the system. Is there a reason it won't let me install? Thanks.

---

### Post by mörgæs on 2018-03-03
How does it work using 17.10.1?

---

### Post by torm on 2018-03-03
I'd rather stick with LTS. If 16.04 won't work with UEFI, should I just wait a month or so for 18.04 LTS?

I did some googling, I have a funny feeling this is a problem when I try to install from the boot menu, but wouldn't be a problem if I do a full install from the Live installer? Am I on the right track?

---

### Post by mörgæs on 2018-03-03
New hardware is best supported by new software. That's one of the reasons why new stuff is released. 

Like all other releases 18.04 is expected to have some bugs when released. 17.10.1 has been around for five months and is about as steady and solid as it gets (provided that you use X11 and not Wayland).

---

### Post by torm on 2018-03-03
I would think that LTS would mean that it would be fully supported until the next LTS. I was hoping to use 16.04 until 18.04 was tried and true. If potential hardware damage is a potential problem with this distro, maybe I should try a different one and switch to xubuntu after the major kinks are worked out of 18.04.

---

### Post by mörgæs on 2018-03-04
> **torm said:**
> I would think that LTS would mean that it would be fully supported until the next LTS. 

Yes, and even further in the sense that one will get fixes for security related bugs. Hardware support is another matter. 

> **torm said:**
> I was hoping to use 16.04 until  18.04 was tried and true.

I would swap 16.04 for 17.10.1 in that sentence.

> **torm said:**
> If potential hardware damage is a potential  problem with this distro

Of course I don't recommend a distro or release which causes damage. 17.10 could under certain circumstances but 17.10.1 is the most bug fixed of all Buntus.

I still think that a live boot of 17.10.1 is the best test you can do. Can't help you more.

---

### Post by torm on 2018-03-04
I did a live boot of 16.04 and it worked fine. Would I have different (better) results if I used the installer in the live boot rather than trying to install from the boot menu?

Also, my main concern with 17.10 is that support ends in July, and I would rather wait until 18.04 has been tested for about 6 months before switching over. This would leave me in the lurch one way or another for about three months.

---


---
title: "GRUB2 and LiveCDs"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by steevk on 2009-10-24
Hello. I'm trying to build my own custom LiveCD, and I'd like to use GRUB2, just like 9.10 does. Unfortunately, there's very little information out there at all, and I don't know enough about how Ubuntu itself is made to find out how it's done.

Could anyone point me to any kind of resource on this?

EDIT:

Turns out that instead of generating my own stage2_eltorito.img, I should have just used the one stored at /boot/grub/stage2_eltorito. Combined with [this blog post](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/#comment-14154), I got it to work.

EDIT again: 

Ooops. Turns out that was GRUB legacy, not GRUB2. Still haven't gotten it yet.

---

### Post by VMC on 2009-10-24
> **steevk said:**
> Hello. I'm trying to build my own custom LiveCD, and I'd like to use GRUB2, just like 9.10 does. Unfortunately, there's very little information out there at all, and I don't know enough about how Ubuntu itself is made to find out how it's done.

Could anyone point me to any kind of resource on this?

EDIT:

Turns out that instead of generating my own stage2_eltorito.img, I should have just used the one stored at /boot/grub/stage2_eltorito. Combined with [this blog post](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/#comment-14154), I got it to work.

I know that [RIPlinux]("http://news.softpedia.com/news/R-I-P-Linux-9-1-Comes-with-Opera-10-and-GRUB-2-114044.shtml") has a grub2 menu driven program. You might look at their sources.

---


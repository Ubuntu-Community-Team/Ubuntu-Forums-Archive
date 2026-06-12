---
title: "Can't boot Ubuntu after new installation"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Marija2811 on 2012-12-11
Hi everyone,

I really hope someone can help me, cause I'm kind of getting desperate. I installed Ubunto on my Netbook, everything went fine, the OS is installed, however, I can't get to it because the booting process doesn't seem to be working properly.
I tried boot-repair, however that didn't work. I hope someone can help me, here's the link I got from boot-repair:

[http://paste.ubuntu.com/1425010/](http://paste.ubuntu.com/1425010/)

Thanks!
Marija

---

### Post by Bucky Ball on 2012-12-11
Welcome to the forums. 

I see nothing amiss in your paste bin output, unless I'm missing something (and I was, see Update below) although not sure why you have an extended partition containing only a /swap partition ... you can have four primary partitions max but the extended partition is normal and good. 

What exactly is happening? You don't give much of a description except the boot doesn't seem to be working properly. Can you be more specific? Blank screen? Are you getting to a menu at boot then crashing? Login screen?

* Update: I take that back. What is happening with sdb1? What is that? The install CD or DVD or a hard drive or USB dongle? Remove it if possible and try again. You have an error with 'Unknown Boot loader on sdb1' so perhaps your machine is attempting to boot from there.

---


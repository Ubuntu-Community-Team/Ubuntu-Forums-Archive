---
title: "Re: Dual Boot with SATA and IDE, Need Help!!"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Dan Kay on 2007-03-13
Hey....Helpful Community!
OK....
I've got 1 SATA drive (160GB) for a Windows Vista install, and 1 IDE drive (40GB) for a Ubuntu install......
I've read several threads on the topic of dual boot with two HDD's and two operating systems,
and I realize there are many schools-of-thought on the subject. Everything from GRUB will take care of everything to GRUB editing and more. No exact science I understand, but alot of very helpful conversation.

At least I don't think I'll have any master, slave issues. (I hope):confused: 

But why shouldn't it be totally straight forward? I may just be simple-thinking thou.
Well I'm armed with tons of info to work from...trial and error....and I must say, being a total nOOB this will be an experience! (you must learn by doing)

Any helpful thoughts or helpful threads you guys may suggest before I start would be greatly
loved. Wish me luck!:lolflag:

---

### Post by jellyfisharepretty on 2007-03-13
Hey Dan Kay,

Bear in mind that I haven't tried dual booting with vista, only with XP.  That being said here's what I suggest :

1. Install visa on your SATA drive (labelled "sda" in linux probably)
2. Pop in the ubuntu live CD and choose to install it on the IDE drive (these are labelled "hda, hdb, etc.)

Hopefully Ubuntu will detect vista on your SATA drive and put automatically the entry in GRUB.  Anyway, it worked for me with XP.  If it doesn't then there are ways to do it manually.

Let me know how it goes,

Good Luck !

---

### Post by gus sett on 2007-03-14
see if the following thread helps:  search on triple boot vista
and check the mdoyle entry :arrow: 

> **Dan Kay said:**
> Hey....Helpful Community!
OK....
I've got 1 SATA drive (160GB) for a Windows Vista install, and 1 IDE drive (40GB) for a Ubuntu install......
I've read several threads on the topic of dual boot with two HDD's and two operating systems,
and I realize there are many schools-of-thought on the subject. Everything from GRUB will take care of everything to GRUB editing and more. No exact science I understand, but alot of very helpful conversation.

At least I don't think I'll have any master, slave issues. (I hope):confused: 

But why shouldn't it be totally straight forward? I may just be simple-thinking thou.
Well I'm armed with tons of info to work from...trial and error....and I must say, being a total nOOB this will be an experience! (you must learn by doing)

Any helpful thoughts or helpful threads you guys may suggest before I start would be greatly
loved. Wish me luck!:lolflag:

---


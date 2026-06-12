---
title: "How to add swap to install process? 16MB Ram!!!"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by Avicus on 2004-10-21
I have a laptop with 16 mb ram, is it impossible to install Ubuntu on it (I know the mem spec is too low according to the requirements, but I am stubborn)?
Can I just somehow add a swap partition to the boot line off the install cd-rom?
Has anyone dared to try a computer with this litttle ram?

---

### Post by anotherdisciple on 2007-10-31
I'm not sure how to do it.. but RAM isn't that expensive... it would be easier on you and your hard drive to buy some. Otherwise it will be writing to your disk like crazy... that can't be good on it.

---

### Post by linuxbz on 2007-10-31
You might want to try something like [Damn Small Linux]("http://www.damnsmalllinux.org/") on it.  It's supposed to be able to run on something with as little as 16MB RAM.

Personally, I always take the Minimum Hardware Requirements given by any OS and double them as a realistic minimum.

And if you have a laptop with 16MB of RAM, I would be surprised if you could still find a RAM upgrade for a laptop that old.

I don't know, but I doubt that Ubuntu installs are looking for swap during the install process.  Basically, if you use the LiveCD, you have an entire Ubuntu system running in RAM. If you use the Alternate install CD, there is still a small Linux system running in RAM.  But since part of the install process is to set up your swap partition(s), it can't assume there is one available until after it completes the partitioning phase at least.

The installer is open source, so I suppose you might be able to hack it to work off swap, but I would have no idea how to do it.

---

### Post by oldos2er on 2007-10-31
Seeing as how the OP is three years old, maybe he's still installing it!!

---

### Post by linuxbz on 2007-10-31
> **oldos2er said:**
> Seeing as how the OP is three years old, maybe he's still installing it!!

Ooops ... I didn't notice that.  16MB wasn't **quite** so underpowered 3 years ago. :)

---


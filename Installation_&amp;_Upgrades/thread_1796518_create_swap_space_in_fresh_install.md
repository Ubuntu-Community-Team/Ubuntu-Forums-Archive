---
title: "create swap space in fresh install"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2011-07-03
i was using wubi installer to dual boot with windows 7. Now i want to have a fresh install with dedicated partition. But while installing that way, the installer tells that i do not have any swap space available. I do not what is that and how to correct it. Please help.
Thanks.

---

### Post by mikewhatever on 2011-07-03
Swap is a small partition, usually about the size of RAM that is used for swapping unused data out of RAM as well as for storing data when suspending to disk. If you don't have it, you'll have to create it during the installation. That said, you you have 2GB of RAM or more, and if you do not suspend to disk, swap may not be needed at all.

---

### Post by malakar.subhendu on 2011-07-04
I have 4gb ram and don't use the suspend to hard disk, but i use suspend to ram. So should i neglect the swap space?

---

### Post by 1clue on 2011-07-04
Swap is used for a lot of things on modern systems, but that doesn't mean you need it.

I'm not familiar with your hardware, but on my system I have actually used swap exactly once, the last day I had 6G RAM.  If you only use your computer for normal everyday stuff, then you could probably get by without it.

If you want swap, you need at least one partition on at least one storage device which is of type 82, which is Linux Swap.

Once you have created the partition(s), you need to do something like this:
**mkswap /dev/sda2** where /dev/sda2 is the partition I made for swap.  This formats the partition so it can be used.

Finally, type **swapon /dev/sda2** to get the benefits immediately.

In order to have your swap come on at boot, you need to have something in /etc/fstab like this:

**/dev/sda2 none swap sw 0 0**

---

### Post by mikewhatever on 2011-07-04
Yep, IMHO, you'll most likely never need swap.

---

### Post by Luke M on 2011-07-04
If a swap partition is not essential then why does the installer insist that you must have one?

---

### Post by 1clue on 2011-07-05
You got me there.  I've wondered about that for years.

At one point I was under the impression that the memory management didn't behave well without swap, but I seriously doubt that's still the case.  It sounds like a bug that they would have fixed almost immediately.

More recently I have been using tmpfs for a whole lot of stuff, which uses swap to store regular files in.  Which means that I still have a swap partition and I still use it, even though I can count the number of times my system actually used swap for the "traditional" purpose on one hand and still have most of my fingers left unused.

---

### Post by Luke M on 2011-07-05
> **Luke M said:**
> If a swap partition is not essential then why does the installer insist that you must have one?
 
Correction: the installer does not insist on a swap partition. I thought it did, but in fact you can continue installation without creating one.

---


---
title: "Adding RAM"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by indiana_crook on 2011-11-17
So I'm adding more RAM to my system.  The computer will show a blank screen after booting and I can't do anything from there.  Is there something I need to do, or do I have to reinstall Ubuntu after adding the RAM?

---

### Post by darkod on 2011-11-17
It should work staright away. Unless you have a bad stick of ram or the new ram doesn't work good together with the old. Try booting only with the new sticks for example. And if that works, than boot with one stick at a time to find a faulty stick.

---

### Post by indiana_crook on 2011-11-17
> **darkod said:**
> It should work staright away. Unless you have a bad stick of ram or the new ram doesn't work good together with the old. Try booting only with the new sticks for example. And if that works, than boot with one stick at a time to find a faulty stick.

Well, I dual boot and Windows comes up just fine.  Also I can boot off a USB and everything works fine.  The fully installed version of Ubuntu is the only thing that is giving me trouble.  I thought the same thing, that it would just work.  Do you think it could be the swap?

---

### Post by darkod on 2011-11-17
I don't see what would the swap partition have to do with it. Anyway it works even without swap.

I'm puzzled, I still say try only the new ram first. Sometimes linux detects problems that windows doesn't (or ignores) and the other way around. Just because one OS is booting fine it doesn't mean all is fine.

One thing is sure: adding ram does not require reinstall.

---

### Post by indiana_crook on 2011-11-17
> **darkod said:**
> I don't see what would the swap partition have to do with it. Anyway it works even without swap.

I'm puzzled, I still say try only the new ram first. Sometimes linux detects problems that windows doesn't (or ignores) and the other way around. Just because one OS is booting fine it doesn't mean all is fine.

One thing is sure: adding ram does not require reinstall.

Puzzled... That's exactly where I would say I am at.  LOL!

---

### Post by indiana_crook on 2011-11-17
> **darkod said:**
> I don't see what would the swap partition have to do with it. Anyway it works even without swap.

I'm puzzled, I still say try only the new ram first. Sometimes linux detects problems that windows doesn't (or ignores) and the other way around. Just because one OS is booting fine it doesn't mean all is fine.

One thing is sure: adding ram does not require reinstall.

Well, it will work with 3GB of RAM... When I try to install the 4th it has the blank screen after boot and it doesn't matter which stick of RAM I remove or which slot I remove it from.  It will boot with only 3GB of RAM or less.

---

### Post by collisionystm on 2011-11-17
Your computer probably does not support 4gb of ram.

Go to [www.crucial.com](www.crucial.com) 
It will spec out your computer.

---

### Post by indiana_crook on 2011-11-17
> **collisionystm said:**
> Your computer probably does not support 4gb of ram.

Go to [www.crucial.com](www.crucial.com) 
It will spec out your computer.

It does, I looked into that before I purchased the extra RAM.  The BIOS is acknowledging the 4GB of RAM, but the system will not boot.  I don't know what the problem is, but I guess I'll just run on 3GB of RAM until I get a new system.  Thank you all for your help!

---

### Post by darkod on 2011-11-17
Very weird. Even if you have a 32bit OS installed which can't use all of 4GB memory, it still works and it can use approx 3.5GB.

---

### Post by gordintoronto on 2011-11-17
Have you tried booting a liveCD and running memtest overnight?

---

### Post by efflandt on 2011-11-17
By default the grub menu in any Ubuntu has memtest86+ listed.  Have you tried using that to test the RAM for some time to see if any errors crop up?

Many years ago I bought some OCZ RAM on sale at Frys and it was almost compatible with my early Athlon64 3200+, but not quite. I think it would lock up sometimes, but I don't recall what memtest86+ revealed. I contacted OCZ and they sent me a slightly different model RAM (same speed) that they guaranteed would work, and it did.

We had Crucial RAM on a older PC at work that would occasionally blue screen XP, even after hard drive was replaced.  When the PC was being retired I finally got around to testing it with memtest86+ and that showed errors.  That PC got no errors with its original insufficient 256 MB RAM, and the Crucial RAM that had errors on that PC lives on without any memtest errors at all on another PC.

So sometimes memory incompatibilities can be a mystery even if it appears to be the proper type and speed. And some memory is more compatible at a greater number of different speeds.

---


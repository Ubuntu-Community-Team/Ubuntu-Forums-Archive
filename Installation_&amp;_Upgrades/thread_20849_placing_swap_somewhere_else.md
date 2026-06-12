---
title: "placing swap somewhere else"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by eraos on 2005-03-18
I'm setting up a Linux file/media server (75% for fun, 25% because it may actually be useful) and it's been built from old and spare parts.

So I have a 2.5 gb hard drive and a 40 gb.

I want to use the 2.5 as the main drive with the 40 gb as the storage depot.  (Direct me if this is a bad idea).  But the main problem I can forsee is running out of space on the master drive.  

Would it be possible--if I installed the system on the 2.5gb-- to mount a useful swap partition on the slave drive?

---

### Post by bored2k on 2005-03-18
[QUOTE=eraos]I'm setting up a Linux file/media server (75% for fun, 25% because it may actually be useful) and it's been built from old and spare parts.

So I have a 2.5 gb hard drive and a 40 gb.

I want to use the 2.5 as the main drive with the 40 gb as the storage depot.  (Direct me if this is a bad idea).  But the main problem I can forsee is running out of space on the master drive.  

Would it be possible--if I installed the system on the 2.5gb-- to mount a useful swap partition on the slave drive?[/QUOTE]
 Yeah why not ? You can partition the 40gb and create off it a 800mb [or whatever] size partition and use it as swap with no problems.

It's more or less how I have things running here .

---

### Post by az on 2005-03-19
It all happens in your fstab...

---


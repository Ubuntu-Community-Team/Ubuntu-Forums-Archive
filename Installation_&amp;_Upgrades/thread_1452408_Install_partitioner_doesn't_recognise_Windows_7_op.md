---
title: "Install: partitioner doesn't recognise Windows 7 operating system."
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by mattyjk on 2010-04-11
[[IMG]http://img.mobypicture.com/c2ec983cb6cc361115f334410cfc0aeb_new_medium.jpg[/IMG]]("http://img.mobypicture.com/c2ec983cb6cc361115f334410cfc0aeb_full.jpg")

So if anyone can point me to a solution it would be great.

---

### Post by mattyjk on 2010-04-12
I just noticed something. The size of the disk that the installer is trying to install on is 1tb. It is looking at my external hdd.

I will go though the steps again but with my external drives disconnected. Will let you know how it goes.

---

### Post by mattyjk on 2010-04-12
it solved the problem.
But I still don't know why it did it.
All I can think of that was different was that I now have Windows backup data and a system image on the external drive. 
I don't know if this is causing it but that is all I can think of.

---

### Post by mattyjk on 2010-04-13
It isn't because of the Windows back up data. It looked at another external drive before it looked at the C: drive. 

Is this a default thing?

---

### Post by Mark Phelps on 2010-04-14
> **mattyjk said:**
> It isn't because of the Windows back up data. It looked at another external drive before it looked at the C: drive. 

Is this a default thing?

It depends on the "order" in which Ubuntu believes the drives are attached to the machine.  For example, if the external drive is known as "hda1" and the internal drive is known as "sda1", then the external drive will show up "first" in the list of drives.

---

### Post by mattyjk on 2010-04-14
makes sense

---


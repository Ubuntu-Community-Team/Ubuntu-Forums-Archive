---
title: "two os on one hard drive"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by fillintheblank on 2008-11-26
I hope I have the right place for this, but anyway. I'm rather new to Ubuntu, and I read that it was possible to install alongside another OS. Last night I tried to figure out how to do this and got as far as the partitioning of my hard drive. From there I am unsure as to what to do to retain my current os as well as install Ubuntu alongside it.

---

### Post by Paul41 on 2008-11-26
See if this helps.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by fillintheblank on 2008-11-26
Unfortunetly I couldn't find the command to resize my partition. the only options were "use entire drive" "use largest continual freespace"(which didnt work) and "manual"(which i am hesitant to use).

---

### Post by snova on 2008-11-26
It's "manual". It's nothing special, it just gives you more precise control over the installation, including a partitioner.

The process, I think, is to resize the existing partition, create a new one in the free space, and install Ubuntu to the new partition.

Be careful. You could lose all of your data by installing to the wrong partition.

---

### Post by oldos2er on 2008-11-26
> **fillintheblank said:**
> Unfortunetly I couldn't find the command to resize my partition. the only options were "use entire drive" "use largest continual freespace"(which didnt work) and "manual"(which i am hesitant to use).
  
 You have to go manual in order to do what you want to do. It's a good idea to backup any data you don't want to lose first.

---

### Post by partsdale on 2008-11-26
the one you are hesitant to use is what you are looking for.. make sure you defrag Windows (some people say to do it twice) before you start the install of linux. There are lots of guides on how to proceed, and yeah it's a little scary but it's not too bad

---


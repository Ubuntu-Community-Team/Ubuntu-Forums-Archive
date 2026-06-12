---
title: "Upgrading while keeping the Home"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Elderlygent on 2008-07-18
Would some kind person give me a simple, step-by-step How To in response to this question:

I'm running Gutsy and would like change up to Hardy. But I'd like to keep my Home directory. Starting from Manual how do I divide up the partitions in order to do so.

Currently, my System Monitor shows I have:

/dev/sda1 /media/sda1 fuseblk 

/dev/sda2 /           ext3

/dev/sda3 /home       ext3

sda 1 is my XP.

The size of the partitions is immaterial. I'm happy with the way they are now.

I am not going to attempt an upgrade having tried it once and, like a lot of people, had the process freeze. So I'm going to download, burn a CD and do a proper install.

Thanks in advance.

---

### Post by Pumalite on 2008-07-18
Go Manual and use the old partitions, but DO NOT FORMAT /home. You can ignore /swap.

---

### Post by Elderlygent on 2008-07-18
> **Pumalite said:**
> Go Manual and use the old partitions, but DO NOT FORMAT /home. You can ignore /swap.

Thanks for that. How do I avoid formatting HOME?

---

### Post by jabeez on 2008-07-18
> **Elderlygent said:**
> Thanks for that. How do I avoid formatting HOME?

Make sure you don't check the "Format" checkbox next to /home.

---

### Post by Pumalite on 2008-07-18
Get going and you'll find it. It's there.

---

### Post by Elderlygent on 2008-07-18
> **Pumalite said:**
> Get going and you'll find it. It's there.

Ok, I'll do that...tomorrow. It's late where I am and I need a clear head. In the meantime. Thanks to Everyone and I'll report back.

Cheers

---

### Post by Elderlygent on 2008-07-19
Yes, well, it wasn't a great success. The advice "keep the old partitions" was fine, except the panel was more complicated than that and, while I thought I'd done it (I didn't format the old /HOME) I hadn't. So I'm back to square one with a single partition plus SWAP. Fortunately I had backed up my old home, so I can copy in my pix etc.

I guess it's hard for an expert to dot all the Is and cross the Ts. But I did ask for a step-by-step.

Cheers

---


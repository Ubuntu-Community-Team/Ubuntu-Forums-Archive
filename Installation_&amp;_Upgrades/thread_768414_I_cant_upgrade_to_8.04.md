---
title: "I cant upgrade to 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Prisma on 2008-04-26
I am using Ubuntu (7.10)

When I tried to upgrade this morning the installer gave me an error message:

> Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 1689M free space on disk '/'. Please free at least an additional 505M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I honestly don't know how to fix this. 

If it is talking about root, how can I liberate more space?? 
My root is 5.58 GB and it has 1.39GB of free space so I guess I need to liberate 505mb to upgrade. How I am supposed to do that?

---

### Post by Pumalite on 2008-04-26
Empty the garbage and run:
sudo apt-get clean
Try again.

---

### Post by Prisma on 2008-04-26
I already did that while ago. I didn't work. :(

---

### Post by khughitt on 2008-04-26
off-topic, but, do you know if it's possible to upgrade using a non-alternative 8.04 cd? I remember having trouble trying to do that with 7.10.

---

### Post by Pumalite on 2008-04-26
> **Prisma said:**
> I already did that while ago. I didn't work. :(
Let's see if we can do something with your partitions:
Pos a screen shot of Gparted

---

### Post by Prisma on 2008-04-26
I cant even install updates on my computer. Instead of installing the update manager only reads them and reload them.  but no installation is conducted. Its that a known bug?

---

### Post by Pumalite on 2008-04-26
System>Administration>Software Sources>Download From>Other>Let it choose thre best for you.

---

### Post by Prisma on 2008-04-26
> **Pumalite said:**
> System>Administration>Software Sources>Download From>Other>Let it choose thre best for you.

Thank you guys for all your responses. 

I already did that as other person suggested in other thread, but it doesn't work either I cant install updates, I have 16 on my update manager. 

When I try to update, nothing happens. They are still listed in the manager. :confused:

---

### Post by TeoK on 2008-04-27
> **Pumalite said:**
> System>Administration>Software Sources>Download From>Other>Let it choose thre best for you.

it's really criminal that this is NOT A STICKY.


Upgrade Manager was a complete failure, with endless freezes and hang-ups and error messages.

Synaptic with "choose your best/fastest server" worked like a charm.

Go Hardy !
fast , smooth , eeeesy on memory!

---


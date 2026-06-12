---
title: "Netvista 6840 Installtion probs"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by puelly on 2007-09-20
I am trying to install ubuntu server on an IBM Netvista 6840 machine and booting from the CD always hangs at "FDC 0 is a post-1991 82077" .  Previously it was hanging at "NET: Registered protocol family 2" but I used the following boot options:

nosmp ide=nodma noapic

I have tried using server 7.04, 6.10 also CENTOS 5.

I am downloading 6.06.1 now to try.

Any suggestions as to how I can solve this problem would be welcome.

Thanks.

---

### Post by Pumalite on 2007-09-20
Could you post your specs. I suspect you memory and graphics are giving you trouble.

---

### Post by puelly on 2007-09-20
Pentium 3 863.9MHz

On board graphics. (No sure)
256 RAM

It was a discarded system that I am trying to breathe some life into

---

### Post by Pumalite on 2007-09-20
With that RAM, this is you best bet>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
It will install easier and run faster in your system
You could boot Live CD, but you would have to make 1 GB swap partition ahead of time and upon installation the system would be sluggish.

---

### Post by puelly on 2007-09-20
I trying to use server edition. that should be low on resources

---

### Post by Pumalite on 2007-09-20
Let's see what happens.

---


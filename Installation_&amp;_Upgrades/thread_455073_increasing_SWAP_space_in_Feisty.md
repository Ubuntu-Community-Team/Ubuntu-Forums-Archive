---
title: "increasing SWAP space in Feisty"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by dphan on 2007-05-26
Hi dears,I am using Feisty with Virtual Box 1.3.8 layered by XPHome and Solaris10. My system Pen4/2.8GB CPU/1024MB RAM/ker-2.6.20.15/SWAP=512MB...
when system boot up XPHome and use more programs, swap space run out up to 100% and make sys snailed down. (85% RAM used, 100% Swap used)

Now I like to extend my swapspace. which is the best solution you trick me please?

my sys partition so now:
/boot 100MB
/ 10GB
/home/ 130GB
/opt 20GB
/tmp 2GB
and /var 2GB
/dev/sda1 is nested for XP Pro (hardly used)

thanks in advance,
D.

---

### Post by steevols on 2007-05-26
Knock a gig or two off of home, and add it to swap with GParted or some other partition editor.. If you've got 1024 RAM, then give yourself 2GB swap.

---


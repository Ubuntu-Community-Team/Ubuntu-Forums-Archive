---
title: "warty to hoary"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-03-16
When the offical version of hoary will be released (April) how will users running warty upgrade to hoary. Will hoary come in to the repositories of users running warty as a upgrade ?

---

### Post by Gary Powers on 2005-03-16
Hoary has different respositories and you must set them up in your /etc/apt/sources.list.  On one box, I took this route and just kept doing (almost every evening)

sudo apt-get update
sudo apt-get dist-upgrade

Worked without problems.  

On my other box, I downloaded the Hoary CD and did a fresh install.  Also worked without problems.

Gary

---

### Post by Martin Atkins on 2005-03-16
I believe (from another thread) that one will also be able to upgrade using
the hoary installation CD.

I.e., by adding the hoary installation CD to /etc/apt/sources.list, using apt-cdrom,
and doing:
   apt-get update
   apt-get dist-upgrade

This sounds like a good approach, for those of us without super-fast internet access!
BUT, I haven't tried it yet...

Martin

---

### Post by kuleali on 2005-03-17
Thank's for all youre help, if everything goes smoothly..i'll se yo in 56m

---


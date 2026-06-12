---
title: "Downgrading from Gutsy to Feisty (7.10 to 7.04)"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by KyleYankan on 2007-07-09
Hi,
 I'm having some issue with my laptop. I'm fairly comfortable within Ubuntu/*NIX, so I thought I would try and give back. I upgraded to Ubuntu 7.10 a few hours ago, and have been spending the whole time trying to fix it. Basically, my wireless support is gone, and several applications keep crashing. What's the least-painful way to revert to Feisty? Is it just to modify /etc/apt/sources.list? That just seems like a painful way to do it, and likely to break something.

Thanks!
 Kyle Yankanich

---

### Post by KyleYankan on 2007-07-09
Victory is mine! Here's what happened:

I installed my Broadcom 4311 driver in Feisty using ndiswrapper. However, being a 43xx card, the bcm43xx driver tried to take over. I simply added "blacklist bcm43xx" to my /etc/modprobe.d/blacklist, rebooted, and voila, the world is good and whole.

Now, I shall begin testing. Thank for the help that was sure to come my way.

---

### Post by chillout15 on 2007-10-13
same here.. a lot of applications kept on crashing and everytime im in the middle of something my laptop freezes..

hope somebody sends updates to correct all the error/bugs involved..

---

### Post by bulldog on 2007-10-13
Personally I think the best way to 'upgrade' is a clean install.
Ofcourse you need to have a separate /nome partition to keep your personal data,but it's the fastest way to do it anyway.

---

### Post by pizzutz on 2007-10-13
I agree, I keep a separate 10gb partition for testing the pre-betas, betas and RCs when I am happy with the performance (or when hardy pre-beta 1 comes out)  I will overwrite feisty with that.  Right now I can boot into feisty or gutsy depending on whether or not I feel like having suspend work on my laptop.:P

---

### Post by kostin on 2007-10-20
How to downgrade to 7.04 from 7.10 with saving of all user settings and data? Is it possible?

There is no FreeNX repo for Gutsy and I want to back to Feisty until new repo doesn`t exists.

---


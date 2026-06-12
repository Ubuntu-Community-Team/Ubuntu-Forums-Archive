---
title: "Dual boot with openbsd."
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by linuxnewbie999 on 2008-06-14
I would like to install Ubuntu8.04 on my current laptop and then install openbsd. I have 60GB hardisk space and i would like to allocate half of the space for openbsd. How do i create the free space for openbsd during the installation of ubuntu ?

---

### Post by Partyboi2 on 2008-06-14
When you get to the partitioning part choose to do it manually then create a / root and a swap partition, I would also recommend creating a /home partition as well, which helps if you ever need to reinstall as you will not loose what is on that partition.
So for example if you have 60 gig hard drive you could create:
/ =10gig
/home =29gig
swap = about 2x the amount of onboard ram but wouldn't go more then 2gig.
Then leave the remaining space till later  to install openbsd.

---


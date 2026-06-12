---
title: "Had Ubuntu and now wont boot"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by mrtickles on 2008-11-06
I downloaded Hardy (8.04) and was trying to get the wireless to work and could not get the updates to work and jumped through hoops trying to get it going and now when I fire up all I get is this:

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+

Everytime I click on one it just reverts back to "press any key" and then shoots me back to the above mentioned

I am at a loss as to how to procede

Please help before (lord help me) windows becomes an option again

---

### Post by Coreigh on 2008-11-06
One possibility is that grub or the menu.1st file (/boot/menu.1st) is messed up or misconfigured.
You said you were jumping through hoops trying to get wireless enabled, what were those steps?

---

### Post by Mark Phelps on 2008-11-06
How about starting by posting the results of "sudo fdisk -lu" here so we can see what partitions you have set up and how they are designated?

---


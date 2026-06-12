---
title: "Risky business ? One shot at installing 7.10"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by jfl on 2008-02-29
[FONT="Comic Sans MS"][SIZE="2"]Hi,
In the past I have successfuly ( I didn't say easily) installed Ubuntu from 6.06 to 7.10 on W2K machines (dual boot).
Actually I must say the upgrade to 7.10 was a breeze - from the live CD - 
**Now the dilemna:**
A friend of mine has finally accepted to try Ubuntu on his new Lenovo laptop running XP pro.
**The catch:** I'll have the machine for one afternoon and it has either to work dual boot or be back in the XP configuration.

The laptop has 3 partitions: C:\ OS   D:\  Apps   E:\Data  plus 1 hidden partition for the rescue. 
I can find 10Gig of available space on both D: and E:.

Even though I have Partition Magic 8.0, I am reluctant to use it, had problem before with ext3.
I believe *gparted* is the way to go ???

Should I create a  */boot*  partition ... I CANNOT clobber the MBR ! because of the rescue partition.
I have never done a dualboot install on a single  disk box.

It is an opportunity that's hard to pass; if it works it will be close to 30 people more in our camp !

What do you recommend ???[/SIZE]
[/FONT]

---

### Post by Pumalite on 2008-02-29
Use Gparted. Don't create a /boot partition. It's going to be tight in 10 GB.

---


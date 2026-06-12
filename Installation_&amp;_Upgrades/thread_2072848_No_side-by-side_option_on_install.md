---
title: "No side-by-side option on install?"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by tonyt3 on 2012-10-18
In the past, when I've installed Ubuntu on a Windows machine, the "side by side" option was there; there's the choice of how big to make the partitions, etc.   However, when I try to install 12.04.1, the option of " side by side with Windows" does not appear on the machine. ?  it is showing the "live CD" performance just fine. This is on an older ThinkPad T400, 160 gig hd, 2 gigs men.
thanks very much
tony

---

### Post by Starcruiser322 on 2012-10-18
Did you try the manual partitioning method?
It's really simple, and allows you to easily shrink your windows partition. It is recommended that you make a logical partition in the free space and make a 2 GB (equal to your RAM) swap partition.

---

### Post by tonyt3 on 2012-10-18
Starcruiser --   thanks ; but when I tr;y to do this, each option says it will blow away the windows partition; there is a small partition (probably the rescue cd section) which is optional to change; but the large partition that has windows on it, -- when I click on that to use, there's the option to change its size does not appear.  I have tried every option several times, and find no appropriate hoop to jump through.  It just does not look like it used to, on the installation routine. bummer
tony

---

### Post by tonyt3 on 2012-10-18
Problem Solved! :-)  I ran Gparted, thinking I would partition the drive before installing Ubuntu, and got an error message that I needed to run chkdsk /f to clear up a problem with the windows partition; so I did, and then the installation routine ran like clockwork.
  the problem was much less obvious than I had expected.
So thanks for your suggestions.

---


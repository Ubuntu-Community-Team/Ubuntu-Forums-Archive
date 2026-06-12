---
title: "Install issue on 64bit, not appearing on 32bit"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by RevenNL on 2011-03-16
Hey guys,

I'm just starting out with Ubuntu 10.10 on the desktop, (got VPS experience) and I'm running into an issue when installing Ubuntu 64bit. One that I'm unable to reproduce with the 32bit (x84/i368) disk. Just to note, the ISO's and disks have been checked with matching MBR.

I'm able to run the live CD on both versions perfectly. However when I press next after the 3th step of installation (The one in which you can choose whether you want to install updates and 3th party software or not), the Ubuntu 64 bit version stalls. Ubuntu doesn't freeze or anything, but it just doesn't seem able to go to the next step. (Partitioning)

The odd thing about is that I can access the step perfectly on the 32bit disk. Now here is the question..... What could be the clarification for this issue and would it be possible to resolve it? (If so, how?)

Thanks for your time!

Martijn (RevenNL)

P.S. Attached you can find a dxdiag output of the laptop. It's an Acer Aspire 7520G.

---

### Post by RevenNL on 2011-03-17
Hey guys,

Just reporting that I solved the issue by reburning the same image on a DVD instead of a CD. It's a weird solution, but it worked.

Just posting it here in case others run into the same issue. :)

---

### Post by sikander3786 on 2011-03-17
Welcome to the forums :-)

Yes that might have been caused by a bad burn. Always burn your discs at the lowest possible speeds and verify the discs afterwards. This page will help most of us.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

Hope you enjoy your stay with Ubuntu!

---

### Post by Skaperen on 2011-03-18
You could check the burn quality by doing "md5sum /dev/sr0" or whatever device your CD/DVD is on.  You can do that while running that CD/DVD as a live device.

I have found that DVD media is of higher quality than CD media the past few years.  Manufacturers have figured out how little dye they can get away with for a certain level of unreliability, and some of them go on the short side.  That and they are using dyes with lower contrast (but to be fair, the better azo dyes degrade in sunlight a lot faster).  DVDs use the better dyes, and at least for now, still use more of the dyes.  As a practice, I always burn using DVD+R media, unless I need to make a red book audio CD, which is virtually never.

An alternative for reliable "burns" is USB memory stick flash drives, or their cousins the camera memory cards (effectively the same if your computer can boot from them, which it probably can if they are attached via a USB adapter).  We just need to get the Ubuntu people to start making hybrid images that can work either as an ISO or a flash drive image that can be directly copied, while unetbootin still works if that is preferred (it has failure modes on badly pre-formatted media).

---


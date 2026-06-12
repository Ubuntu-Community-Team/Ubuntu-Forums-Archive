---
title: "Ubuntu -&gt; Mac external drive"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by peter.h.m.brooks on 2013-11-17
I've managed to get Ubuntu running on a USB stick with dropbox on windows quite easily. Anything beyond that has taken hours and not got me very far. I've read, and tried, all sorts of advice about how to set up bootable USB memory sticks. I've been back to Ubuntu 10.04.5 server (I'd tried 12.04.03 & 13.10 as well) in the hope that diskutil would find a disc system that would work. I've used hdiutil to create .img files.

I've even created a new partition on my hard drive and dd'd the ISO and .img files there in the hope that the boot process would recognise it (I've installed rEFIt, so I've a more complicated boot process now), but it gives the 'missing OS' message or a missing file iso..

What I'm wanting to do is have an external disc (I've got a 3TB LaCie USB 3.0 drive) with a bootable linux partition. I'd like to use that either to boot from my Macbook pro or from a Dell laptop. Then I'd like to run a virtual copy of windows from it. Alternatively, I'd be happy running a virtualbox version.

I've got a windows system on my Mac, and I've tried configuring the USB drive from there, but I get much the same errors.

I'm not quite sure what to do next. Any suggestions would be welcome.

---

### Post by peter.h.m.brooks on 2013-11-17
Oh, when I try to repair the dd partitions, I get the message (from diskutil):

[FONT=Lucida Grande]Invalid BS_jmpBoot in boot block: 000000[/FONT]

---


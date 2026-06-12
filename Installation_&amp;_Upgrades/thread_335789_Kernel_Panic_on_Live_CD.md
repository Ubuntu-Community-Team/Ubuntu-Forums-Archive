---
title: "Kernel Panic on Live CD"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2007-01-10
Here's an odd one.  My system boots into my existing kernel (2.6.19.1) fine, but when I try to reinstall Ubuntu from the Live CD I get a "Kernel panic - not syncing: Attempted to kill init".  This just started...I've been using this system (and reinstalling from the Live CD several times) for several weeks now, and just started having this problem.  Any ideas?  I'm running a memory test (from the live CD) right now.  I also tried burning a new Live CD.

Just as an FYI, here is why I'm trying to start over.  I've been trying to make a Diamond PVR-560 TV card work with IVTV for a couple of months.  This week I was changing some settings for the card in ivtv-cards.c to see if I could make it work.  At a certain point it got to where I couldn't get IVTV to initialize the card at all, because the call to request_irq failed with return code 38.  It even fails that way when I install my working Hauppauge PVR-150 card, and I couldn't figure out what was causing it, so decided to start over.  Do you suppose the two are related (the kernel panic from the live CD and the request_irq error)?  I find it odd that I can still boot from the hard disk, but not from the Live CD.

Thanks,
Rich

---

### Post by 64mgb on 2007-01-10
It looks like I have a mouse or keyboard problem.  If I move the PC (not the mouse, keyboard or monitor) to my other test station, it works fine...both the Live CD and the call to request_irq work fine.  Odd....

Rich

---


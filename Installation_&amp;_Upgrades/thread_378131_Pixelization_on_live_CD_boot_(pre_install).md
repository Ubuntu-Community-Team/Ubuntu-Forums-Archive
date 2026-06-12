---
title: "Pixelization on live CD boot (pre install)"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by SoltoN on 2007-03-06
When I boot the live CD on my main machine, I get what you see on the image below. I can still move the mouse, however I dont get anything else. 

[img]http://bullysquad.ca/4.jpg[/img]

System specs are as follows

Asus A8N-SLI Premium
X2-3800+
2 x BFG Geforce 7800 GT
2 GB ram
2 x 250GB HD in SATA Raid on Nforce raid controlor (onboard)

Any input would be greatly appreciated.

---

### Post by SoltoN on 2007-03-15
does anyone have an idea of whats going on with this one? Its got to be a video driver issue, is there a way to install ubuntu from command line?

thnx again

---

### Post by enochr on 2007-03-16
I've had a similar issue trying to install 6.10 live cd with two 7900GTs installed, I removed one of them, ran the Live CD & installed without issue.

I then ran all the updates, shutdown the system put the second card back in, powered on & selected the updated kernel boot option from the grub menu an the ubuntu booted without issue with two video cards.

Install the latest nvidia drivers & you should be good to go.

---


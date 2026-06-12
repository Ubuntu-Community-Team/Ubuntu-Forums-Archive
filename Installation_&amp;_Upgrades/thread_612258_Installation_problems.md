---
title: "Installation problems"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Eliitehunter on 2007-11-13
This threads must be annoying, but sorry... I haven't been able to solve this by myself :(
I bought a new computer two months ago, and I couldn't boot the live cd. The computer is an E6600, 8800gts 640, 2gb G.skill, p5w dh deluxe, 2 sata disks, 1 ide dvd-rw
I guessed that it was a problem with video, but with the upcoming release of ubuntu I thought it was a good idea waiting for it. The issue hasn't been fixed, I get stuck after the first menu after booting (the "grub-like" menu)

I've been thinking and this problem seems to be caused by video or the faulty ide support the p5w dh has (Jmicron controllers) (Debian installation CD got stuck searching for IDE devices)

Any ideas/help?

Thank you!

---

### Post by taurus on 2007-11-13
You can always try using the alternate CD to install Ubuntu on your machine.

---

### Post by Eliitehunter on 2007-11-13
Yup, it's and option. But I would like to know the reason why the LiveCD doesn't boot anyway.

---

### Post by Eliitehunter on 2007-11-13
I have just tried with the alternate install CD, and found the problem (but not the solution, though).
The DVD-RW cannot be mounted. Tried forcing the device to ACHI and both PATA and SATA and none of them worked, any ideas?

EDIT: After reading a lot about this mobo's issues, found out that pressing F6 and entering all-generic-ide will fix ide detection. On the other hand, the cd was corrupted so I couldn't install it. I'll post as soon as I get some news

---


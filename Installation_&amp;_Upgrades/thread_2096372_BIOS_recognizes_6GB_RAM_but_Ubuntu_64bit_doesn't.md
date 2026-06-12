---
title: "BIOS recognizes 6GB RAM but Ubuntu 64bit doesn't?"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by tommaxwell on 2012-12-19
Hey Ubuntu users!

I recently bought a new laptop because I wanted to get into Ubuntu, but I'm having a problem. I originally installed 32bit and didn't realize until later that I would need 64bit to fully support my 6GBs of RAM. After going through the installation process again, this time with 64bit, the 6GB of RAM just isn't showing up -- or at least not all the time. The weird thing is that every now and then, when I check under "About This Computer," it shows 5.5Gig of RAM (which is normal). Also, when I hold down F2 on boot-up it shows that 6GBs of RAM is installed. I tried "free -m" in the Terminal like some suggested but it only shows the 1.5GB (2GB stick) that came with the computer. I tried removing the 2GB stick that came installed but then the computer won't start. I thought that it might be the wrong type of RAM, but if that was so wouldn't BIOS just not show the 4GB stick at all? Also why would Ubuntu recognize it part of the time?

---

### Post by pqwoerituytrueiwoq on 2012-12-19
shared video
your integrated GPU is using some of your ram

---

### Post by tommaxwell on 2012-12-19
Interesting, didn't know the GPU needed 4.5GB of memory.

---

### Post by darkod on 2012-12-19
Even though you say BIOS shows the 6GB, I wonder if the issue is a bad stick of 4GB.

Did you try with only the 4GB stick but in the first slot, where the 2GB came installed? See what that shows in both bios and ubuntu.

---

### Post by pqwoerituytrueiwoq on 2012-12-19
> **tommaxwell said:**
> Interesting, didn't know the GPU needed 4.5GB of memory.
now this is definitely off
make sure your ram is plugged in all the way
run memtest86+ the copy with ubuntu 12.10 has a bug on test #7
[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

---

### Post by CharlesA on 2012-12-19
If you see the memory in the BIOS, then the machine can see the memory.

Please post the output of free -m.

---


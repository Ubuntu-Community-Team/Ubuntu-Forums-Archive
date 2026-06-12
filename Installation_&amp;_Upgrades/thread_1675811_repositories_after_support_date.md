---
title: "repositories after support date"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by vwbug on 2011-01-26
I have Ubuntu 9.10 on my PC and am really happy with it.  As you know, support ends in April. I can't upgrade to 10.04 or 10.10, tried several times, it just doesn't like my old video card. Money is really tight now, so can't upgrade the video card either:(

OK, now my question.  Are the repositories still available after the support date?

Thanks

---

### Post by howefield on 2011-01-26
Yes, the end of life repositories are moved here..

[http://old-releases.ubuntu.com/ubuntu/dists/jaunty/](http://old-releases.ubuntu.com/ubuntu/dists/jaunty/)

You won't get security updates, but the software in the repository will still be available to you.

---

### Post by cipherboy_loc on 2011-01-26
What type of video card is it? It could be that there are extra packages that you need to install on the newer Ubuntu (10.xx)  to make it work. 


Cipherboy

---

### Post by vwbug on 2011-01-26
> **cipherboy_loc said:**
> What type of video card is it? It could be that there are extra packages that you need to install on the newer Ubuntu (10.xx)  to make it work. 


Cipherboy

Think I've tried everything.  Just too much to fix.  The easy way would be to buy a newer card.  I have a NVIDIA MX4000 64mb. Tried with and without the NVIDIA drivers. Anyway I'm happy with my 9.10 for now.  Played with some other distros and had the same problem.  Must be the new kernel.

---

### Post by cipherboy_loc on 2011-01-26
Is there an option in the BIOS to set how much memory your graphics card gets? On my laptop with ATI graphics (default from Dell), I set it to 128MB, and it works just fine, but I have issues if I decrease it by much (even though I run Fluxbox).


Cipherboy

---

### Post by cascade9 on 2011-01-26
> **vwbug said:**
> Think I've tried everything.  Just too much to fix.  The easy way would be to buy a newer card.  I have a NVIDIA MX4000 64mb. Tried with and without the NVIDIA drivers. Anyway I'm happy with my 9.10 for now.  Played with some other distros and had the same problem.  Must be the new kernel.

Nope, it wasnt the kernel, itwas xorg. The version shipped in 10.04+ didnt work with the nvidia drviers (and IMO canonical should have removed the 96.xx drivers from the repos for 10.04+ untill the problem was fixed)

As far as I know, nvidias newer 96.xx drivers do work with the newer xorg in 10.04/10.10 now.

---


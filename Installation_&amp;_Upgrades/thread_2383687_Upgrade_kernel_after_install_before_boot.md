---
title: "Upgrade kernel after install before boot?"
date: 2018-01-28
forum: Installation &amp; Upgrades
---

### Post by tomwolf on 2018-01-28
I have a kernel panic when I try to boot ubuntu server after an install. The issue has been fixed upstream but since I can't boot up ubuntu a first time, is there any way to upgrade the kernel before doing that?

---

### Post by DuckHook on 2018-01-28
Welcome to the forums, tomwolf.

If it is a new install, you haven't anything to lose by doing a fresh install. Especially if server, it takes all of less than 10 minutes on my machine. However, if you have upgraded or there is some time already invested in an old install, then you can chroot into the borked system using a LiveUSB and upgrade that way. Instructions for chrooting follow: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by tomwolf on 2018-01-28
This happen on a fresh server install with anything from 16.04 to 18.04 so doing a fresh install isn't a solution I'm afraid. I will try to do a fresh install and use the chroot method even if I haven't gotten to the login screen. Thanks for the welcome and the answer =)

---

### Post by DuckHook on 2018-01-28
> **tomwolf said:**
> This happen on a fresh server install with anything from 16.04 to 18.04 so doing a fresh install isn't a solution I'm afraid.
This is very unusual. A fresh install should not have the wonky kernel which I thought might have been the problem.
> **tomwolf said:**
> …The issue has been fixed upstream…
Would you mind describing what you think that fix is? If you can, please link to the info/site that describes what this problem is and what the fix may be. Also, please give us your HW specs. The more detailed, the better, especially with respect to CPU, MOBO, GPU, etc.

---

### Post by tomwolf on 2018-01-28
The bug was reported and found here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1726519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1726519)

From what I understand it was fixed upstream and is now in the hwe kernel but since I install server I don't get the updated kernel. It seems to be a very unusual panic. 
I have a Supermicro SC826 2U 2xE5-4617

---

### Post by deadflowr on 2018-01-28
You can install from a mini.iso and it'll install the latest kernel.
Mini installs and server installs are much the same except for the fact a mini has to download everything.
Mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by tomwolf on 2018-01-28
Using the mini.iso in expert mode I managed to install with kernel 4.13.0-32 and it booted up just fine =) Thanks for your help. I'm sure I'll be back sooner rather than later with more questions.... ;)

Tomas

---


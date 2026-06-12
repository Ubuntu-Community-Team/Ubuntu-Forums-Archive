---
title: "Update Manager crashed while updating, system now unusable"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by McMuffin1892 on 2012-06-09
I recently installed Ubuntu 12.04 (a fresh new installation, not an upgrade), and of course I had to run the updates once it was installed. While installing the updates, the update manager crashed. Now, my system is effectively unusable. Every time I start up my system, within 10 seconds of logging in, it tells me "A system error has occured", and then it tells me "Update Manager has crashed", then it gives the same message for every single application I have installed. Attempting to start up any application gives an immediate "[Application] has crashed".

I'm thinking I should just do a new installation, but I'm worried the exact same thing will happen again.

Not sure if this is relevant, but I'm running a 32-bit installation despite the fact that my laptop is 64 bit (it's a HP Pavilion dv7). I've had a total of 3 64 bit Ubuntu installations before on my laptop, and I found that all of them were extremely glitchy, so I decided to just use a 32-bit because from what I've heard, 32-bit Ubuntu is more stable.

---

### Post by McMuffin1892 on 2012-06-09
Also, something else I should add.

Installing ubuntu is usually a difficult task on my laptop. The installer usually crashes midway through installation. Each time, it crashes the first few times then succeeds on the fourth or fifth attempt.

I've been using USB installation with PenDrive Linux every time because the CD/DVD burner on my desktop computer (which is my main computer--laptop which is having issues is my "side" computer) is broken.

---

### Post by darkod on 2012-06-10
Can you boot the recovery mode entry? If you can, it should show you a small menu.

In that menu select Network to activate the network (internet), then select Drop to root shell.

That will load a command prompt as root.

Then you can try something like:
```
dpkg --configure -a
apt-get install -f
```

Usually that can help with broken packages. See how it goes.

If you have only ubuntu and the grub2 boot menu doesn't show at boot, hold Shift and it should show. There you can select the recovery mode.

---

### Post by McMuffin1892 on 2012-06-11
That fixed it. Thanks!

---

### Post by darkod on 2012-06-11
No problem. Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---


---
title: "Boot problems after installing Sabayon on dual boot with Lucid"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by ubukool on 2010-05-11
Hi everyone,

I've recently installed Sabayon in dual boot with Lucid but Sabayon trashed my grub I can't get either of them to boot.  When I boot up, I just get the grub prompt.  I've tried lots of things including reinstalling grub.  The latest thing I did was to get grub to find my installs and make a new grub.cfg so I tried: 

sudo update-grub

and I got the message:

grub-probe: error: cannot find a device for /

So now I'm stuck.  Does anyone have any ideas how I can get a dual boot between Sabayon and Lucid going grub-wise? Thanks for your help. :)

---

### Post by ubukool on 2010-05-11
Hi everyone,

It's fixed :)  Next time I tried to boot into Lucid Lynx, grub gave me a menu and I was able to boot no problem so grub is properly installed and working.  I then had a brainwave that the  

grub-probe: error: cannot find a device for /

message was because my Sabayon partition wasn't mounted so grub couldn't see it.  I mounted it and did an 'update-grub' and grub could see all my kernels and partitions.  For those who are having a similar problem, just make sure all your partitions containing distro filesystems are mounted before updating grub.  I haven't checked but I assume my grub.cfg file is now up to date.

P.S, how do I mark this thread as 'solved'?

---


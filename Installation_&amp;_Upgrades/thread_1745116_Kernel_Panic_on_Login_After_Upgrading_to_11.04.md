---
title: "Kernel Panic on Login After Upgrading to 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by patfortytwo on 2011-04-30
I've just upgraded my Asus eeePC netbook from 10.10 to 11.04, and I am unable to login to my primary account. I think it may have something to do with the nm-applet. I've done the following:

- upgraded and restarted
- on login, the machine crashes soon after the ubuntu startup sound. Hard reset was required. I tried this about 5 times with the same result each time
- after a reset, I used Alt+F2 to login from a console. This worked fine
- then tried logging in to my secondary account (in gnome). This worked fine. I've never used this account to connect to my wireless router, so the nm-applet icon showed no connection (as expected)
- from within secondary account, I switched user to my primary account. This worked fine, but there was no nm-applet icon in the panel (presumably because the secondary account was still logged on?)
- from within the secondary account, I tried to connect to my wireless network and the same kernel panic occurred
- reset the machine, and selected an older kernel from within grub (2.6.35). I was then able to login to my primary account and connect to my wireless router, and from there to the Internet

So is this something to do with the 2.6.38 Kernel and my wireless drivers? I'd obviously prefer to use the most recent kernel, but have no idea how to diagnose or resolve this issue. Any assistance would be much appreciated

Thanks

---

### Post by mörgæs on 2011-05-01
Hi, welcome to the fora.

How does the machine work in a 11.04 live boot?

When downloading the ISO, best is to take it from a torrent.

---

### Post by patfortytwo on 2011-05-01
Hi

Thanks very much for the response. I tried as you suggested and booted from an 11.04 Live USB drive. It suffers from the same problem though i.e. it boots up fine, but as soon as I try to connect to my wireless router I get a Kernel panic.

Any suggestions?

---

### Post by mörgæs on 2011-05-01
A kernel panic is as bad as it gets in Linux. 

You can reinstall 10.10 (which I would do myself) or keep booting into an old kernel in 11.04. If you choose the latter, you will receive kernel updates, and some day you will get one that works.

---

### Post by patfortytwo on 2011-05-01
Ah well. I'll stick with 11.04 (it has some updates that I need) until the bug is fixed. Is there somewhere I should post this issue so that it gets noticed by the people who do the fixing? 

Thanks for your help

---

### Post by mörgæs on 2011-05-01
Yes, you can post in Launchpad:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by teachop on 2011-05-01
> **patfortytwo said:**
> Hi

Thanks very much for the response. I tried as you suggested and booted from an 11.04 Live USB drive. It suffers from the same problem though i.e. it boots up fine, but as soon as I try to connect to my wireless router I get a Kernel panic.

Any suggestions?
Does this seem like the same thing?  [https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/762496]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/762496")

---

### Post by patfortytwo on 2011-05-01
Yes, that looks like exactly my problem (Asus 1001p, wifi and WPA2). It seems like this is on the radar and a fix has been identified. 

Thanks very much :)

---

### Post by laerub18 on 2011-05-10
hey, i had the same problem, here are my findings:

[http://ubuntuforums.org/showthread.php?t=1751928](http://ubuntuforums.org/showthread.php?t=1751928)

---


---
title: "Ubuntu 10.04LTE x86_64 hangs on start-up."
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ExpatUK on 2010-05-02
Hello there chaps,

Complete unix novice here, I haven't really touched unix since RedHat 6 before the turn of the century, and have been a completely happy Windows user for 15 odd years - infact it was my profession for 12.

I successfully installed 9.10 (32-bit) on my old Acer Aspire 9504WSMi with no drama whatsoever, and happily used it with XBMC... which leads me to where I am now.

I just rebuilt my HTPC system and decided to give running Unix on it a try (the motherboard is a Gigabyte GA-G41M-ES2H). I installed my usual Windows 7 set up - all set up without drama, lovely. Installed 9.10 64-bit... had various issues with things just not playing as nicely as on my laptop (I assumed it was just a difference in chipsets and the such like rather than an x86/x64 issue), so I decided to run the 10.04LTE release.

Well, that's where things get... weird.

I've reinstalled (and reformatted the unix partitions) the thing about 10 times in the last 36 hours... different result each time. I'd say 8 of the times I was successfully able to get to desktop and tinker around. 

Haven't had a single issue with dual-booting (just thought I'd clarify that as there seems to be a lot of GRUB issues with 10.04).

What I'm experiencing is summed up exactly in **the first paragraph** this bugtracker post:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502599/comments/2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502599/comments/2)

(I do not enter into any reduced graphics mode or have any troubles like that at all.)

It happens pretty much every time I reboot Ubuntu now, GRUB loads fine and then I get the lovely cursor in the top-right corner with no HDD activity. It seems to happen less frequently if I do a soft-reboot (without powering off), however it's far from reliable. 

Being an HTPC the majority of the direct access I do is via VNC (which has caused problems in itself regarding the master key ring... in the end I just disabled password auth to get around it, but I did not have this issue in 9.10!) and SSH (a complete novice still) from my main Windows 7 box.

Please help a die-hard Windows user get something functional out of his HTPC & Ubuntu. I was so put off by my experiences of unix in the past (RedHat 6) I really didn't bother with it until recently, but I was *so impressed* with Ubuntu and XBMC on my laptop I'm dying to get this working on my HTPC!

You'll probably need to hold my hand a bit, but I can follow clear instructions! :D

Thanks in advance,

Expat

**Edit:** Sorry, I meant to clarify that I'm also using a PCI-E ATI HD4550, and I have this bug with or without the proprietary drivers (in fact, the OSS ones seem a lot more... 'polished'.)

---

### Post by ExpatUK on 2010-05-03
Shameless bump.

---


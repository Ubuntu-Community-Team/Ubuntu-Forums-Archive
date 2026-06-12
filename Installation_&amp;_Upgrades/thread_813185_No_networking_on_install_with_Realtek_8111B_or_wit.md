---
title: "No networking on install with Realtek 8111B or with Intel Pro1000"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by brendan.lefoll on 2008-05-30
Ok I have a problem, I installed ubuntu 8.04 LTS using the alternate installer in 64bit mode on my pc. When I installed I first chose my onboard realtek gig ethernet port and I booted to find no networking. There is also a bug in X on my 7800GTX 256MB so I can't go log into gnome or connect to the net. 

When I ping my gateway I get a Network is unreachable. I reinstalled with my Intel Pro 1000 as the network card (all plugged in ;-) ) and the onboard card disabled in the bios after reading some problems with the wrong driver being detected.

Same think happened. When I do a /etc/init.d/networking restart I get eth0=eth0 ignored or something similar. This was the same with the realtek card. 

Is this something to do with roaming being enabled? How do i make my NICs work? I upgraded my current 7.10 install on my SATA disks on 8.04 but want to reinstall on my adaptec 3000S raid5. However for some reason when reinstalling from scrath the networking simply won't work.

Can anyone help? I've tried to look but have found nothing.

Thanks,
Brendan

---

### Post by dstew on 2008-05-30
[This page]("http://www.jamesonwilliams.com/hardy-r8168.html") shows one way to fix the problem. It looks a little sophisticated. You also need to have the build-essential and linux-headers packages installed I think.

---


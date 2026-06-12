---
title: "Hardy freezes upon logout (ASUS P5E-VM, Intel G35 Video)"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by patis on 2008-04-28
Hello,

I have an ASUS P5E-VM motherboard with an Intel G5 (3500) video chip set on it. Feisty didn't manage the video well, no compiz effects possible, but it never crashed. Hardy improves in that I can now use compiz well.

But, every time that I logout Hardy freezes, completely, nothing to do but a hard reset to get out of this situation.

I am assuming that this has to do with the X windows driver (Intel) since Hardy works fine when I boot single user (no X windows).

I recreated the xorg.conf file using the command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

which gives me a bare bones config file, basically nothing specific defined there. I guess everything is now dynamically found. And it works well when I restart GDM, I can login and work without any problems. But I rather not logout (which makes other members of my family quite unhappy).

So, does anyone have a working xorg.conf file for similar hardware? Any ideas why this freezing is happening?

Thank you,

-- 
Patis

---

### Post by superFerra on 2008-05-01
Hello,
I'm in the same situation!!!
It boots well but hangs when logging out. Sometimes it happens that it doesn't boot at all. To be more precise: it boots till the gdm login screen then hangs. No way to access any console or ssh-in.
I think it's a bios issue. My bios revision is the 0503, i've improved the stability disabling the DVMT technology but not solved the problem.
Nothing interesting into logs (Xorg, dmesg)
Same hardware but 7.10 works nicely (without compiz effects)
Any suggestion?!
Please help

PS: The problem affects both 32 and 64 bit editions.

---

### Post by AnythingBut on 2008-05-08
Hey,

I've got the same problem as well.  It might be helpful to chime in at [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/228242](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/228242) to confirm the bug.

superFerra, what sort of improvements do you find when you change the DVMT settings?

---

### Post by niQo on 2008-05-12
I also had the same problem.
First of all, I thought that was a bug related to intel driver, so I updated to 2.3.0 from debian experimental but it didn't solve the problem.
Yesterday I have updated to bios 505, and do some ubuntu minor upgrade and now my system is working fine ! (no more hangs when logout).
I hope it will help.

Edit:
I added a new user on my system, switched between two users and my system has freezed again :( So, bios upgrade doesn't fix this.
(but logout, restart and shutdown don't freeze anymore)

---

### Post by AnythingBut on 2008-05-12
Hi niQo,

I'm using BIOS v. 505 and still have the problem.  Are you still using the newer Intel driver?

---

### Post by niQo on 2008-05-12
AnythingBut: I'm still using 2.3.0 intel drivers.

---

### Post by AnythingBut on 2008-05-12
Hi niQo,

Do you know if that upgrade to 2.3.0 included updates to DRM or any other kernel modules?  Or was it just X.org drivers?

---

### Post by niQo on 2008-05-12
xserver-xorg-video-intel package contains only X.org drivers. But, it seems that this bug is related to the kernel.
A possibly related bug : [http://bugs.freedesktop.org/show_bug.cgi?id=15714](http://bugs.freedesktop.org/show_bug.cgi?id=15714)

---

### Post by sippnonacorona on 2008-05-18
I also had problems with freeze-up on a black screen after logging out until I changed video settings. On bootup, I added vga= with a VESA number that supported the resolution of my monitor to the grub menu.lst file . When HARDY installed, it did not properly set my video configuration when it detected the unsupported GMA X3500 Intel chipset used on this mainboard. This chipset seems to be very new and I expect there to be native drivers showing up soon in a future upgrade.

---


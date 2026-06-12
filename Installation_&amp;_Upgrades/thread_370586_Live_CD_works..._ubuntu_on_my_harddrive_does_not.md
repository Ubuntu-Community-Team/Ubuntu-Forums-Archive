---
title: "Live CD works... ubuntu on my harddrive does not"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by chris_ak on 2007-02-25
Hello,
This is the third distro I've tried in the last two days.  Suse, and Mandriva were what I tried before this.  Both worked okay except for sound.  Ubuntu has working sound on the live cd at least so I'd really like to get this up and running.  Okay down to the problem.  I can run the live cd fine when I select 1024x768 - 32 rather than vga avoiding the infamous blank screen.  However, after I installed ubuntu and rebooted I would again encounter the blank screen after the initial ubuntu splash screen finished. I think what I need to do is edit my xorg.conf but I haven't even been able to get a complete boot in recovery mode.  On top of that I'm not exactly sure what I need to change.

Specs:
HP dv6040us
 AMD Turion 64
Nvidia GeForce 7200 Graphics card

Any help would be greatly appreciated. Thanks in advance.

---

### Post by chris_ak on 2007-02-26
SUCCESS!
Well I fixed my problem whatever it was.

Booted in recovery mode

apt-get update
apt-cache search nvidia

apt-get install "*nvidia driver*"

nvidia-xconfig

reboot


done!

---


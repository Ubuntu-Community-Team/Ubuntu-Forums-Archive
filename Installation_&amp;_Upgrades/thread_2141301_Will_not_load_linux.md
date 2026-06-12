---
title: "Will not load linux"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by Jeroen De Dauw on 2013-05-02
I have a Samsung Series 9 NP900X3A-A03US laptop on which I put a brand new Kubuntu install last week, using the 12.10 x64 image. This installation included using full disk encryption for the whole disk.

After installation was done (ie Kubuntu was working, and I had restarted onceafter which it was still working), I changed the order of the devices to boot from. On restart, Kubuntu would no longer load. Instead of showing the full disk encryption dialog, I'd just sit there doing nothing. I decided to not lose time on this and just reinstalled the thing, after which I put on a bios password and did not change the device boot order. All was fine.

Now I gave this laptop to my mom, and after a few days, she has the same issue. Before it broke, she mistyped the full disk encryption passphrase 3 times and then hit crtl+alt+del to restart. And now it won't load...

So when this device boots, it shows a "boot menu" thing with as only option "ubuntu", and when picking that one, it now no longer actually loads kubuntu. It'll have a cursor blinking ath the top left of the screen for half a second after hitting enter on this dialog, and that is all that happens afterwards.

I have no idea what is causing the issue, how to debug it, much less fix it. Any help would be greatly appriciated.

---

### Post by MAFoElffen on 2013-05-02
If you want to go to recovery mode menu from your boinked grub menu:
At grub menu, press "e' to get into edit mode > Arrow down to the line that starts with "linux". > Replace all after ro ("quiet splash $vt_handoff") with "recovery nomodeset".

If you want to try booting the Linux kernel to a TTY text console to verfiy you can boot... and to diagnose and correct from a commandline:
At grub menu, press "e' to get into edit mode > Arrow down to the line that starts with "linux". > Replace all after ro ("quiet splash $vt_handoff") with "--verbose single".

If that all fails, boot from a Kubuntu LiveCD and follow the instructions in the second half of post 3 of my Graphics Resolution Sticky (link in my sig line) to root to your installed sys, diagnose and make changes to it.

---


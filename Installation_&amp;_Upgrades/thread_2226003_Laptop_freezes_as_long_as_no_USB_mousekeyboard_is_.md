---
title: "Laptop freezes as long as no USB mouse/keyboard is connected"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by z0ttel on 2014-05-24
Dear all,

I have an old laptop which I still would like to use for small tasks (browsing the internet). Because Windows XP ran out of support, I decided to install a lean version of Linux - XUbuntu 14.04 LTS - on it. The installation went fine, but now I've got the problem that the laptop crashes/freezes at the login screen, if no external input device like an USB mouse or an USB keyboard is connected. 
What's actually happening after startup is: the startup to the grub menu is fine, then the splash screen is shown correctly and finally the login screen is shown for a couple o seconds. If there are no external devices are connected, the screen will freeze, turn black or show strange graphics. The laptop completely freezes and is not accessible - even not via sshd or X forwarding over the network. This problem occurs with XUbuntu and LUbuntu, I've tried the versions 14.04 LTS and 12.04 LTS non-pae.

Here are some details regarding the laptop:
Fujitsu Amilo M1420
Pentium-M 1,7GHz (=> Dothan, 400MHz FSB, no PAE)
Radeon Mobility 9600
1GB of RAM installed

I assume that the issue is somehow related to the graphics driver (radeon), because if I boot using the paramters "nomodeset xforcevesa", the crash/freeze is not happening. Unfortunately, the native resolution (1280x800) can't be selected in this mode.

Attached to this post you'll find the dmesg and Xorg logs which have been captured after the laptop has been started with and without an external USB mouse connected. I've also added a screenshot of some error messages which showed up after the laptop has been booted without mouse and did crash.
I would like to kindly ask you to have a look on these logs and the error trace; I'm not completely unfamiliar with Linux/Ubuntu, but I wasn't able to find anything unusual.


Thank you!
Oliver

---

### Post by mörgæs on 2014-06-05
What happens if you boot with nomodeset only?

---

### Post by z0ttel on 2014-06-06
It is basically the same behaviour. Sometimes the login screen is shown and I can type some characters of the password, but the laptop freezes nevertheless. Sometimes I can move the mouse but it is very 'laggy' - it jumps all over the screen. When the laptop is in this 'condition'; I can't enter anything into the login window any more; also switching to other VTs is not possible. Sometimes, the screen shows strange graphics

---

### Post by z0ttel on 2014-06-07
Update: The issue is solved now. I had to use radeon.agpmode=1 as a boot parameter and now the system works without any connected devices. This seems to be an old problem; using the correct search string "radeon mobility 9600 agp mode" leads to the technical background and this solution

---

### Post by sudodus on 2014-06-07
Thank you for sharing your solution :-)

---


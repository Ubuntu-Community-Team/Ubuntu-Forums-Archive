---
title: "Ubuntu 16.04 - 18.04 upgrade fails -- critical pkg could not be installed"
date: 2018-08-23
forum: Installation &amp; Upgrades
---

### Post by dwilde1 on 2018-08-23
I have been avoiding upgrading from 14.04 because of issues with 16.04 (flashing screen).

I finally decided to bite the bullet. The 16.04 upgrade seemed to work with no issues. I tried compiling and running a program in my Eclipse CDT, and it successfully worked. My Firefox seemed to work fine although Facebook locked up on me once. I had to do a hard reset. This is a generic Dell i3 laptop with 4GB.

Thinking I was okay, I did sudo apt-get update / upgrade one more time, and sure enough, it wanted even more updates and a reboot.

Started upgrade-manager. It did say that the 18.04 upgrade is 'recommended'. I proceeded.

The first failure was fontconfig, then it failed in installing 'systemd'. Realizing that not having that would probably hose the system, I tried to do damage control.

Can't get ALT-F2 to work, it changes sound volume. Can't open a terminal window, so I couldn't run ubuntu-bug. My SciTE text editor won't save and crashes regularly. Gedit won't launch at all.

Final error message is:

[B]Could not install 'systemd'

The upgrade will continue but the 'systemd' package may not be in a working state. Please consider submitting a bug report about it. :(

triggers looping, abandoned[/B]
some Python utilities, until I closed the bu
The fontconfig message was identical except for programname.

The upgrade halted unpacking some Python utilities  until I closed the bug warning window.

I do have another 14.04 system but I'll have to take down my Doze box for its KB, mouse and monitor.

---

### Post by dwilde1 on 2018-08-23
It didn't reboot into nowhere-land, but the screensaver did activate and authentication fails in a weird way. The auth box shows 'Reply' in it but when I click it goes directly to displaying an 'Authentication failed' message.

---

### Post by dwilde1 on 2018-08-27
Solved it with a fresh install. Not perfect, but at least 18.04 mostly works.

---


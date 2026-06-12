---
title: "Reboot doesn't complete, have to power cycle"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by beredim on 2013-02-07
Just finished installing Ubuntu 12.10 on a Toshiba Satellite L300-1EF laptop. This is a dual boot installation alongside Windows 7 Pro.

The problem I have is that when I try to reboot the machine (from Ubuntu) the reboot process hangs, apparently right at the end. That is the progress bar dissappears, the screen switches off, no hard disk activity, no keyboard response (dead Caps Lock key). However the reboot never actually completes, the machine is frozen, and I have to power cycle the machine using the power switch.

This behavior appeared both at the first reboot required post-installation and at the second reboot required post-upgrading, and persists even after everything has been updated.

Other than that everything appears to run smoothly. The described behavior only appears on the Ubuntu side of the installation. Windows reboots work without problem, and shutdown (regardless of OS) completes normally also.

- Any suggestions on resolving this reboot issue?

- Any logs that I can post to make it easier to solve

---

### Post by linuxtechguy on 2013-02-07
You will have to make note of where it is getting stuck. Try hitting the esc key if you dont see anything on the screen. Take a picture with a digital camera if you can or write down what is the last thing you see on the screen.

You could try looking through dmesg output or /var/log/messages but there might not be any information.

---


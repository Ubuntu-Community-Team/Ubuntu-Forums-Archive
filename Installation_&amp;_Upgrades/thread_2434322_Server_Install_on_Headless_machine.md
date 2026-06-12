---
title: "Server Install on Headless machine"
date: 2020-01-03
forum: Installation &amp; Upgrades
---

### Post by Frozen001 on 2020-01-03
I am playing around with an older WD Sentinel DX-4000 that I want to install Ubuntu Server on.  This is headless, but I have gotten access to a serial debug port on TTY1.  Now all I need is to somehow redirect the output from the USB stick installer to output to the console on TTY1.  From searching others how have done this they say that you have "to change Grub to output to the console and add “console=ttyS1,115200n8” to the boot command"  so where do I do this?  do I have to blindly type this or can I somehow add it to a file on the USB image?  I am trying to use 18.04.3 server.

---


---
title: "NVIDIA module problem"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by kekojeep on 2008-08-19
Hi there, I'm having some trouble getting Ubuntu to work with the Nvidia drivers. I'm using Ubuntu 8.04, 64 bits, with a Geforce 7900GS, using two monitors configured in TwinView.

The problem is, I installed the NVIDIA driver from their website, but every time I start Ubuntu, I get the graphics error screen, a low resolution and the graphics configuration screen. If I get to other terminal, kill GDM, remove NVIDIA module (rmmod NVIDIA) and reload it by (modprobe NVIDIA), then I restart GDM and I get the NVIDIA driver logo, boots with correct resolution, correct configuration of the monitors, Compiz works flawlessly, but I lose my keyboard setup, which I quickly change and everything works, but doing this each time I boot Ubuntu is getting annoying.

Trying to configure the driver on the initial "graphics error" screen doesn't help.

Can anyone give me a tip on what could be causing this mess? From reloading the module, I can see the driver is working, but I can't figure out why it craps out on normal boot.

Appreciate any help,

Thanks

André Tomasi

---


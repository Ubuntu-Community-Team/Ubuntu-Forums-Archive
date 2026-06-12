---
title: "New x64 install, can't log in: mouse unresponsive."
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by LancerNZ on 2013-02-14
I've decided to upgrade my install of Ubuntu LTS from 32 bit to 64 bit, backed up the /home dir and gone for gold.

When I boot into my newly installed system, the mouse is laggy and won't allow me to click the "login" button (no response to LMB). I have an advanced GPU (EVGA GTX580-Classified) and I think I'm hitting the issues as brought up here: [http://askubuntu.com/questions/138722/12-04-gpu-lockup](http://askubuntu.com/questions/138722/12-04-gpu-lockup)

The problem is, the solution requires internet access. Until I get into GUI to configure my USB modem, I don't have that.

...so, without using the internet, how can I fix the problem that I can't log in? I don't thing grub options are present, though I'm sure I should be able to install/tweak grub from the installation CD - right? I do have the original Ubuntu install CD, which I can run successfully when opting for a "nomodeset" option.

EDIT: I do have internet - through USB stick to wireless, but only when running through the live-CD. On the actual install (e.g. booting from the new install hard drive), I can use CTRL-F2 to get a terminal (escape the bad login screen), but the USB wireless access isn't working.

---

### Post by LancerNZ on 2013-02-14
Okay - so what's needed is to hold the SHIFT key down while to computer boots from hard drive. From here I can now see the grub options and pressing "e" allows me to enter "nomodeset" to the bootup line (just before "quiet"), then F10 to boot. This is only temporary and I will need to permanently add nomodeset to full grub options later.

But this does allow me to now boot into the new system, and my USB wireless works from there, allowing me to upgrade packages etc. :D

---


---
title: "Ubunu Unity 23.04 install problems on hp EliteDesk 800 g1"
date: 2023-04-25
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-04-25
Has anyone been able to install 23.04 or other recent versions of Ubuntu on an hp EliteDesk 800 g1?  After convert HDD to GPT, turning on UEFI, and changing BIOS security to settings recommended on other websites. I am still getting the following error:

[  0.224764] pnp 00:01: can't evaluate _CRS: 12311

At this point, the PC is locked up and will not respond to Ctrl-Alt-F2 or Ctrl-Alt-Delete.  PC has to be turned off to restart.  PC is dual-boot with Win Pro 64.  Grub display is correct.  Operation under Win 10 is perfect. BIOS is v02.77 dated 4/17/2019.

Apparently something (BIOS setting) is keeping Ubuntu from loading.

Please let me know what I have missed or made incorrect settings.

Thank you,

John

---

### Post by stepphon on 2023-05-04
I am having the same issue is there any movement on this?

---

### Post by ActionParsnip on 2023-05-04
Does it prevent booting?

---

### Post by cigtoxdoc on 2023-05-04
Yes, the system locks up with the error message I gave previously.  Even Ctrl-Alt-Del won't restart the system.  Have to turn off and restart.  PC is dual-boot with Win 10 64 Pro.  Win 10 Device Manager list two display adapters: Intel HD Graphics 4600 and NVIDIA GeForce GT 610.

I can get to Ubuntu root shell prompt.  I need the command lines to remove the NVIDIA GT 610 drivers and make sure that the PC reboots with the nouveau display driver.  Based on my experiences with other PCs, once the NVIDIA driver is gone, the system will reboot into 23.04 without a problem.

Thank you in advance.

John

---

### Post by ActionParsnip on 2023-05-05
```

apt --purge remove nvidia*

```
Should do it

---

### Post by cigtoxdoc on 2023-05-05
Thank you ActionParsnip.  It solved problem.  John

---

### Post by ActionParsnip on 2023-05-05
> **cigtoxdoc said:**
> Thank you ActionParsnip.  It solved problem.  John

Great news. Remember to mark the thread as solved if the issue is sorted

---


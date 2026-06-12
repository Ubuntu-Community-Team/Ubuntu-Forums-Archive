---
title: "Thinkpad R61 blank screen"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by pcheng on 2007-07-13
I am trying to install Ubuntu on my Thinkpad R61. I got an error which says /bin/sh: can't access tty but I can fix that with doing modprobe piix or by changing the SATA BIOS configuration to Compatibility. But after that the screen goes through the boot procedure and when it reaches the point to start x-windows it goes black and nothing happens. I try to go to the text prompt using CTRL+ALT+1 through 8 but nothing happens.

I am downloading the alternate CD to try a text based setup but I thought I'd post a message here just in case someone can help me out.

The R61 I have has the nVidia NVS 140 graphics adapter.

Please let me know if you have any ideas.

Thanking you in advance.

!Update! I installed the alternate CD and everything seemed to go fine. When I rebooted I get to the Grub screen and when I go to xwindows it hangs with a blank screen.

---

### Post by erikdalen on 2007-08-07
I have the same problem with my Thinkpad R61, 1680x1050 widescreen model (8918-5QG).

I've tried both with the open source and proprietary nvidia driver with no success. Text mode works though, and the VESA driver.

---

### Post by sanders_muc on 2008-07-15
Hi Erik,

have you solved the problem by now? I am thinking about buying a Thinkpad R61 8918, and wonder if a current Ubuntu runs fine on it.

Thx
  Simon

---

### Post by erikdalen on 2008-07-15
Yes, this issue has been solved now since quite a while with the nvidia-glx-new driver in Ubuntu. All hardware works except the fingerprint reader which is a different model than in earlier thinkpads. There has been posts on the fprint mailing list though about a guy reverse engineering the driver for it, so there is hope though.

---


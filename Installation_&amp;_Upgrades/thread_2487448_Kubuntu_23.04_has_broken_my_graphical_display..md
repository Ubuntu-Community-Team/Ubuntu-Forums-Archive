---
title: "Kubuntu 23.04 has broken my graphical display."
date: 2023-06-05
forum: Installation &amp; Upgrades
---

### Post by davidsinfield on 2023-06-05
I recently updated to Kubuntu 23.04 and now the boot stops with a "Cannot Display This Video Mode. 1280x1204 recommended"

I've tried SSH to the pc but the boot stops before the SSH server is loaded.

The default install disables the grub menu so I cannot boot into recovery mode to remove nouveau and install the nvidia-340 driver.

I've booted from a live usb (22.10) in and I get the same error.

I can boot the live USB in safe graphics mode and[FONT=courier new] lspci | grep ' VGA ' [/FONT]gives:

[FONT=courier new]02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [NVS 300] (rev a2)

[FONT=arial]I'm not sure where to go next. Any suggestions?[/FONT][/FONT]

---


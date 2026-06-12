---
title: "linux 3.0.0-1-amd64 kernel boot problems"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by bulva on 2011-11-03
I can't boot kernel 3.0.0-1 on Asus G53S, it freezes when booting around 10th second with: 

```
NVRM loading NVIDIA Unix x86_64 kernel module 275.28
```then after some time it displays

```
udevd[350]: timeout: killing 'usb_id --export /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/video4linux/videob' [994]
```to eventually restart. Both the kernel and NVIDIA proprietary driver are coming from repositories. The message from dkms suggested that the module got configured fine when installing new kernel headers. 

I have no such problems with an old 2.6.32 kernel, yet I could use asus wmi driver that comes with new kernel, for better fn keys support and keyboard backlight that do not work with 2.6.32.

---


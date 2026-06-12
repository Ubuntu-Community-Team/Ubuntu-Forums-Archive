---
title: "neopi air neo ubuntu 16.04 upgrade?"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by josephchrzempiec on 2022-10-20
Hello,, I had this neo pi air neo for some time. I just never got around to working with it. I was searching around and found out it has ubuntu 16.04 on it. It only has 512MB of memory and 8Gb of memory. All I'm using it is for the i2c and SPI pins plus a few other GPIO pins. 

my question is I was wondering If it will support the latest ubuntu If I upgraded it? Also I was wondering snese it says it had two USB broken out pins does anyone know if these USB work out of the box if I added a USB header to it, Or do I need to do something within the OS to enabe them?

Joseph

---

### Post by MAFoElffen on 2022-10-21
It was built to run Ubuntu "Core". Ubuntu "Core" 20.04 and 22.04 will run in 256MB with 256MB of storage...

The GPIO pinout for USB is
```

[TABLE="class: table table-condensed table-bordered table-responsive"]
[TR]
[TD]Pin #[/TD]
[TD]Name[/TD]
[TD]Description[/TD]
[/TR]
[TR]
[TD] 2[/TD]
[TD] USB-DP1[/TD]
[TD] USB1 DP Signal[/TD]
[/TR]
[TR]
[TD] 3[/TD]
[TD] USB-DM1[/TD]
[TD] USB1 DM Signal[/TD]
[/TR]
[TR]
[TD] 4[/TD]
[TD] USB-DP2[/TD]
[TD] USB2 DP Signal[/TD]
[/TR]
[TR]
[TD] 5[/TD]
[TD] USB-DM2[/TD]
[TD] USB2 DM Signal[/TD]
[/TR]
[/TABLE]

```

---

### Post by josephchrzempiec on 2022-10-23
Thank you.

---


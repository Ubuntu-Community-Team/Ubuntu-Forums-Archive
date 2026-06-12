---
title: "Dual screen broken after upgrade to 17.10"
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by arussel on 2017-11-13
Hi all,

 I have a simple dual screen setup that use to work nicely before the upgrade to 17.10. After upgrade, with both screen pluged in, the boot hangs. If I start with a single screen and plug in the second after login, I can move and see the cursor on the new screen, I can see the screen in the settings but the screen stays completely black. For info:
 ```
lspci -nn | grep '\[03'00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM] [1002:6811]
```

What else can I provide to help debug that problem ?

Alex

---

### Post by arussel on 2017-11-18
is there any more info I can provide ?

---

### Post by darran-kelinske on 2017-11-25
Having a similar issue with a Radeon HD 6850

---


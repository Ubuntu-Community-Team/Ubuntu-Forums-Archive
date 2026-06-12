---
title: "Cannot boot using nomodeset"
date: 2019-10-09
forum: Installation &amp; Upgrades
---

### Post by icecreamharbor on 2019-10-09
Hello, I am installing ubuntu 16 on a windows 10 machine. I have successfully done this before several times on other machines. However this time I met a new problem.

PROBLEM: When I choose try ubuntu during the usb boot, I will see the following message:

[COLOR=#000000]Couldn't get size: 0x800000000000000e[/COLOR]
[COLOR=#000000]MODSIGN: Couldn't get UEFI db list[/COLOR]
[COLOR=#000000]Couldn't get size: 0x800000000000000e
[/COLOR]
After google search I find that my CPU without a integrated graphics may be a reason. And the solution is to use nomodeset. However, I tried adding nomodeset but still it cannot boot and I got the same message above. I have tried adding nomodeset before/in the middle/behind the quite splash words or replacing the words, but nothing works. Hoping anyone could give me some suggestion. Thanks in advance.

NOTE:
CPU: AMD Ryzen 5 3600
MOBO: MSI B450M MORTAR TITANIUM
GPU: EVGA RTX 2080 SUPER XC ULTRA

Secure boot disabled
Fast boot disabled

---

### Post by ubfan1 on 2019-10-09
The Ryzen 3 series has all sorts of issues. FIRST -- ensure your motherboard firmware is up-to-date.    You should try a later release like 18.04 at least.  The later kernels in 19.04 or even beta 19.10 might help.

---

### Post by icecreamharbor on 2019-10-10
Thank you very much! The 18.04 works.

---

### Post by rajath-walter on 2019-11-02
Hey can you tell me the detailed steps of how you got 18.04 working on a pc with ryzen 5 3600.
My PC specs:-
CPU- ryzen 5 3600
GPU- Amd vega 56

---

### Post by The Cog on 2019-11-02
This may be relevant: [https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
As ubfan says - motherboard firmware needs to be up to date - assuming your motherboard manufacturer has released an appropriate update yet.

---


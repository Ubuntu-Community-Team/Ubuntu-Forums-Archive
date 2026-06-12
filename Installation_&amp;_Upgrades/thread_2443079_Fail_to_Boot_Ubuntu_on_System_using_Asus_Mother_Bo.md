---
title: "Fail to Boot Ubuntu on System using Asus Mother Board"
date: 2020-05-11
forum: Installation &amp; Upgrades
---

### Post by juanbuntu on 2020-05-11
This morning I ugraded from Ubuntu 19.04 to 20.04. After the upgrade finished, system can't finish booting. It shows a black screen, with the Ubuntu Logo at the center bottom of the screen and he Ubuntu "waiting" animation on top of the Log.

The hardware on the system is as follows:

[COLOR=#000000][FONT=Calibri]Asus Prime X370-Pro for AMD Ryzen AM4 CPU[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]AMD Ryzen 7 1700 CPU with Spire Led cooler: [/FONT][/COLOR][COLOR=#000000][FONT=Calibri]8 cores, 16 threads[/FONT][/COLOR][COLOR=#000000][FONT=Calibri] 4 MB/16MB cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]EVGA SuperNova 650 G2 80+ 650 W Power supply[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Corsair Vengeance LPX 16 GB (2x8GB) DD4 DRAM @ 3000MHZ[/FONT][/COLOR]
 [COLOR=#000000][FONT=Calibri]EVGA GeForce GTX [/FONT][/COLOR][COLOR=#000000][FONT=Calibri]1060 [/FONT][/COLOR][COLOR=#000000][FONT=Calibri]6GB SSC GAMING ACX 3.0, 6GB GDDR5, LED, DX12 OSD Support (PXOC)

Any help, suggestions, most welcome. Thank you [/FONT][/COLOR]

---

### Post by ajgreeny on 2020-05-11
How did you do the upgrade?

19.04 to 20.04 is not an offered upgrade and will never be so. I imagine therefore that you manually edited the sources changing from whatever d name 19.04 was called to focal, a move that is not recommended and is likely to cause problems.

However, as you have an nvidia graphic card you may need to boot with the nomodeset option. Try that a d sè if it gets you to a GUI, then install the recommended driver from Additional  Drivers.

---

### Post by juanbuntu on 2020-05-11
Thank you. Could you please tell me how  I may boot using the  nomodeset option?

---

### Post by juanbuntu on 2020-05-11
1. Actually, the software updater offered the upgrade to 20.04, so not sure why you said it was not offered and will be never there.

2. I tried booting with the "nomodeset" option. No difference. Same problem.

---


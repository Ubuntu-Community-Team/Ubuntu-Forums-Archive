---
title: "geforce drivers for karmic koala"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by redzsky on 2009-08-25
does anyone know which graphics driver works for geforce go 7400 for karmic koala has anyone got them to work ,would be well interested?they were working for jaunty jackalope thanx

---

### Post by zenarcher on 2009-08-25
I'm using the 185.18.36 Nvidia driver with Karmic (64 bit) and it's working fine for me on two different systems.

Cheers,
zenarcher

---

### Post by taavikko on 2009-08-25
> **redzsky said:**
> does anyone know which graphics driver works for geforce go 7400 for karmic koala has anyone got them to work ,would be well interested?they were working for jaunty jackalope thanx

Yes, "aptitude show nvidia-glx-185" will show you every supported GPU's
by that package.

```
 The following GPUs are supported: GeForce 6800 Ultra, GeForce 6800, GeForce
 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT, GeForce 6800 GT,
 GeForce 6800 GS, GeForce 6800 XT, GeForce 7800 GTX, GeForce 7800 GTX, GeForce
 7800 GT, GeForce 7800 GS, GeForce 7800 SLI , GeForce Go 7800, GeForce Go 7800
 GTX, GeForce 6800 GS, GeF orce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce
 Go 6800 , GeForce Go 6800 Ultra, GeForce 6800, GeForce 6600 GT, GeFo rce 6600,
 GeForce 6200, GeForce 6600 LE, GeForce 7800 GS, Ge Force 6800 GS, GeForce 6800
 Ultra, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce
 Go 6600, GeF orce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, G
 eForce Go 6600, GeForce Go 6600 GT, GeForce 6200, GeForce 65 00, GeForce 6200
 TurboCache(TM), GeForce 6200SE TurboCache(T M), GeForce 6200 LE, GeForce Go
 6200, GeForce Go 6400, GeFor ce Go 6200, GeForce Go 6400, GeForce 6250, GeForce
 7100 GS, GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra, Tesl a C870,
 GeForce 7350 LE, GeForce 7300 LE, GeForce 7300 SE/72 00 GS, GeForce Go 7200,
 GeForce Go 7300, GeForce Go 7400, Ge Force 7500 LE, GeForce 7300 GS, GeForce
 6800, GeForce 6800 L E, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200, GeForce
 6 200 A-LE, GeForce 6150, GeForce 6150 LE, GeForce 6100, GeFor ce Go 6150,
 GeForce Go 6100, GeForce 7900 GTX, GeForce 7900 GT/GTO, GeForce 7900 GS,
 GeForce 7950 GX2, GeForce 7950 GX2, 
 GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS, G
 eForce Go 7900 GTX, GeForce 7600 GT, GeForce 7600 GS, GeForc e 7900 GS, GeForce
 7950 GT, GeForce 7650 GS, GeForce 7600 GT , GeForce 7600 GS, GeForce 7300 GT,
 GeForce 7600 LE, GeForce 
 7300 GT, GeForce Go 7600, GeForce Go 7600 GT, GeForce 6150S
 E nForce 430, GeForce 6100 nForce 405, GeForce 6100 nForce 4 00, GeForce 6100
 nForce 420, GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8400
 GS, GeForce 9500M GS, GeFo rce 8600M GT, GeForce 8700M GT, GeForce 8400 SE,
 GeForce 850 0 GT, GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeF orce
 8600M GS, GeForce 8400M GT, GeForce 8400M GS, GeForce 8 400M G, GeForce 9400
 GT, GeForce 7150M / nForce 630M, GeForc e 7000M / nForce 610M, GeForce 7050 PV
 / NVIDIA nForce 630a, 
 GeForce 7050 PV / NVIDIA nForce 630a, GeForce 7025 / NVIDIA
 nForce 630a, GeForce GTX 280, GeForce GTX 260, GeForce 8800
 GTS 512, GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS
 , GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS, GeF orce 9600 GSO,
 GeForce 8800 GT, GeForce 9800 GTX, GeForce 96 00 GT, GeForce 9600 GS, GeForce
 9800M GTS, GeForce 9800M GTS , GeForce 9600M GT, GeForce 9600M GS, GeForce
 9500M G, GeFor ce 9300 GS, GeForce 8400 GS, GeForce 9300M GS, GeForce 7150 /
 NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 630i, GeF orce 7050 / NVIDIA
 nForce 610i, GeForce 8300, GeForce 8200, nForce 730a, GeForce 8200, GeForce
 8100 / nForce 720a, Quadr o FX 4000, Quadro FX 4500, Quadro FX Go1400, Quadro
 FX 3450/ 4000 SDI, Quadro FX 1400, Quadro FX 4400/Quadro FX 3400, Qua dro NVS
 440, Quadro FX 540M, Quadro FX 550, Quadro FX 540, Q uadro NVS 285, Quadro FX
 5600, Quadro FX 4600, Quadro NVS 11 0M, Quadro NVS 110M, Quadro NVS 120M,
 Quadro FX 350M, Quadro 
 FX 350, Quadro NVS 210S / NVIDIA GeForce 6150LE, Quadro FX
 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quad ro FX 1500, Quadro
 FX 4500 X2, Quadro FX 560, Quadro FX 370, 
 Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX
 570, Quadro FX 1700, Quadro NVS 140M, Quadro NVS 130M, Quad
 ro NVS 135M, Quadro FX 360M, Quadro NVS 290, Quadro FX 3700, 
 Quadro FX 3600M
```

---

### Post by trulan on 2009-08-25
They are working on the generic kernel, no problems at all here with that.   However, they are not working at the moment on the rt kernel (Ubuntu Studio).

---


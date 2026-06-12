---
title: "AMD Radeon HD 7660G + 7670M Dual Graphic Drivers Installation Problem"
date: 2018-02-04
forum: Installation &amp; Upgrades
---

### Post by deshpande-makrand24 on 2018-02-04
I have AMD Radeon HD 7660G + 7670M Dual Graphics in my Laptop which work perfectly fine when I boot Windows 10. But when in terminal I type

sudo aticonfig --initial -f --adapter=all

It shows

sudo: aticonfig: command not found

also when I check
[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]sudo nano /etc/X11/xorg.conf

The file which Opens is completely BLANK.

So can somebody help me to install graphic drivers on my laptop. I am using Windows 10 and Ubuntu 16.04. LTS Duel Boot.

---

### Post by bcschmerker on 2018-02-05
**Have ye the Package fglrx-driver?**  The Utility /usr/sbin/aticonfig is included with the Advanced Micro Devices® LinUX Graphics Driver and Catalyst&#8482; Control Center&#8482;.  However, it is incompatible with the GNOME® Desktop due to lack of EGL support.

---

### Post by QIII on 2018-02-05
fglrx does not support 16.04.  Development was dropped and fglrx is not compatible with any Linux distribution using the current version of X Server.  16.04 installs with either Radeon or AMDGPU depending on whether the latter supports the GPU detected.  I do not believe either of those models is supported by AMDGPU (or would be by the 16.04 installer, at least).

To see which module is loaded, please post the results of

```
lsmod | grep radeon 
```

and

```
lsmod | grep amdgpu 
```

---

### Post by deshpande-makrand24 on 2018-02-07
The results of

```
lsmod | grep radeon 
```

radeon                      1515520  9
i2c_algo_bit                  16384  1 radeon
ttm                                98304  1 radeon
drm_kms_helper        155648  1 radeon
drm                             364544  12  ttm,drm_kms_helper,radeon


and

```
lsmod | grep amdgpu 
```

is blank

---

### Post by QIII on 2018-02-07
That means that the open source Radeon driver was loaded at install time as expected.  You have the appropriate driver installed and running already.

What issues are you encountering?

---

### Post by deshpande-makrand24 on 2018-02-14
Whenever I try to run videos on my laptop they do not run smoothly. Even low quality videos like 480p videos pixelate while playing or if try to skip forword few minutes.

---


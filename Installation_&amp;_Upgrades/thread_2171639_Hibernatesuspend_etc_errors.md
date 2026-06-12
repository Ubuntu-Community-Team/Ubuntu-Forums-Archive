---
title: "Hibernate/suspend etc errors"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2013-08-31
I'm running Ubuntu 12.04 on a Lenovo ThinkPad T500.  When I close the lid, the system keeps running, although all open applications are killed.  If I choose, say, "Hibernate" from the shutdown menu (I'm using Cinnamon), the screen blanks to a console, which then fills with messages like:

```

radeon 0000:01:00.0 GPU lockup CP stall for more than ... msec
dpm_run_callback(): pnp_bus_resume+0x0/0x70 returns -19
PM: device 00:0a failed to retore: error -19

```

It turns out that device 00:0a is PNP0c31 (whatever that may be!).  Sometimes after the error message the system will shutdown for a second, only to spring back into life immediately (that is, before a lid close/lid open cycle).  Currently the only way I can be sure of successfully saving power is by turning off the machine with its power switch.

It would appear that the issue is somehow related to the graphics driver, so what is my best option here?  FWIW, the command "lspci -v | grep VGA" returns

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650] (prog-if 00 [VGA controller])
```

and "lsmod | grep radeon" returns

```
radeon                832167  1 
ttm                    76326  1 radeon
drm_kms_helper         47459  2 i915,radeon
drm                   240232  7 i915,radeon,ttm,drm_kms_helper
i2c_algo_bit           13317  2 i915,radeon
```

Any help would be very gratefully received!

---


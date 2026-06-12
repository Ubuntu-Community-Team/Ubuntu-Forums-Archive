---
title: "Problems with HDMI"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by bramwerbrouck on 2018-09-01
Hi,
I used etcher to flash a version of Ubuntu 16.04 on my Micro SD card, but when I put it in my RaspberryPI and connect the HDMI cable to my Television I got "Not supported"

in the config file I tried this:
enable_uart=1
kernel=uboot.bin
device_tree_address=0x02008000
dtparam=i2c_arm=on
dtparam=spi=on
hdmi_safe=1

Than I have something like a color-picker on my screen, but nothing more.. What am I doing wrong?

these are th[COLOR=#000000]e specs of my television:
[/COLOR][COLOR=#000000][FONT=-webkit-standard][TABLE]
[TR]
[TD][COLOR=#000000][FONT=Arial]Screen Size[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]32“ (81,28 cm)[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Resolution[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1366 x 768 (WXGA)[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Aspect Ratio[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]16:9[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Display Color[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]16.7 M[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Contrast Ratio[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]750:1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Brightness[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]450 cd/m2[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Viewing Angle (Horizontal)[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]178°[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Viewing Angle (Vertical)[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]178°[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Response Time[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]8 ms[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]HDMI[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]YPbPr[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]S-Video[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Composite[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]SCART[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]2[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]VGA (PC)[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Video Color System Support[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Vivid, Personal, Standard, Sharp[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Tuner Input[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]PAL-SECAM ×1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Video Output[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Composite ×1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]HDMI Line in[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]R/L Line in[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]PC Line in[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Headphone Out[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Audio Out[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]No[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]EQ[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]EE Solution[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Tvia 5600TS[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]3:2 Pull Down[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Auto Detection[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Comb Filter[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]64bit - 2D GUI Engine[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]De-interlace Image Enhancement[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]3D Motion Adaptive[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Noise Reduction[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Picture in Picture[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Language[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]English, German, French, Italian, Spanish (Danish, Finnish, Dutch, Swedish)[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Sleep Timer[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]MTS[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Teletext[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Wide Mode Viewing Aspect Ratio[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]Yes[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]VESA Mounting[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]200 x 100[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Dimension (W x H x D)[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]810mmx 650mmx257mm[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Net Weight[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]19.4 kg[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Power Consumption[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=MingLiU]&#8806;[/FONT][FONT=Arial]194 W[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]Standby Power Consumption[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=MingLiU]&#8806;[/FONT][FONT=Arial]3 W[/FONT][/COLOR]

[/TD]
[/TR]
[TR]
[TD][COLOR=#000000][FONT=Arial]AC Power Supply[/FONT][/COLOR]

[/TD]
[TD][COLOR=#000000][FONT=Arial]AC 100-240 V, 50-60 Hz[/FONT][/COLOR]

[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by tea for one on 2018-09-01
The Raspberry Pi requires an image/OS that is suitable for an ARM processor.

Here is the list of images [https://www.raspberrypi.org/downloads/](https://www.raspberrypi.org/downloads/)

---


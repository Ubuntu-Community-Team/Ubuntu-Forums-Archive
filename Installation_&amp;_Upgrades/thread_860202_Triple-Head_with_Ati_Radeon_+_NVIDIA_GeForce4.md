---
title: "Triple-Head with Ati Radeon + NVIDIA GeForce4"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by mike137 on 2008-07-15
Hi all,

I just wanted to report on a successful triple-head setup in 8.04LTS (no Xinerama, no RandR, etc.)... I have an AGP ATI Radeon 9550 card with VGA + DVI outputs and a PCI nVidia GeForce4 MX 4000 card with VGA output. The monitors are a 22" Dell 2208WFP and a pair of 17" Dell 1703FPS, the tower is a vanilla Dell Dimension 4500 2GHz with 1GB RAM.

Since the ATI/nVidia proprietary drivers are (apparently) incompatible and flgrx is required to get the ATI dual-head working, I enabled 'fglrx' and disabled 'nvidia' in the restricted drivers gui. For the GeForce, the 'nv' driver works fine, except that you can't have desktop effects for the whole triple-head (it attempts to install the 'nvidia' driver, which is a Bad Thing (TM) with this setup).

Here are the relevent lines from lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:0c.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

Note that trying to drive the second ATI output by using the Busid 1:0:1 results in a cloned display. Instead, you need to drive both on 1:0:0 and add a few lines to the driver section.

Also, note that my triple head is a three desktop setup -- ie., three menu bars, etc. No window sharing, just mouse/kbd sharing; and you have to hack the hell out of apps that claim a display like OpenOffice and Firefox to get them open on more than one at a time.

I attached my xorg.conf.

---


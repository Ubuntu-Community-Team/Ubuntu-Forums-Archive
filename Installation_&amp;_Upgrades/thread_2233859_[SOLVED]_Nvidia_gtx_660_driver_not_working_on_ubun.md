---
title: "[SOLVED] Nvidia gtx 660 driver not working on ubuntu 14.04"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by Delliriumy on 2014-07-11
The problem is with nvidia drivers. I battle for quite some time chasing my tail.

Details : 

syslog warning :

"kernel : nvidia: module verification failed: signature and/or required key missing -tainting kernel"

Xorg.0.log :

"NVIDIA(1) : Setting mode "DFP-0:nvidia-auto-select"
"NVIDIA(GPU-0): Display (DELL U2410 (DFP-0) does not suppport NVIDIA 3D VISION"
"NVIDIA(GPU-0):    stereo."

Xorg.1.log :

"(WW) Warning, couldn't open module nvidia"
"(EE) Failed  to load module "nvidia" (module does not exists, 0)"

I can work in ctrl+shift terminals but ctrl+shift+f7 prompts black screen.

---

### Post by grahammechanical on 2014-07-11
Are you installing this driver through Additional Drivers? It seems to me that this is the problem.

> [COLOR=#000000]NVIDIA(GPU-0): Display (DELL U2410 (DFP-0) does not suppport NVIDIA 3D VISION"[/COLOR]

What driver is this?

Regards.

---

### Post by Delliriumy on 2014-07-12
What do you mean by additional drivers? I tried to install from suggested repositories and didn't work at all. Now i installed directly from nvidia drivers webpage for linux.

"What driver is this?"

[http://www.geforce.com/hardware/technology/3d-vision](http://www.geforce.com/hardware/technology/3d-vision)
And it have some problems with U2410m which is LCD DELL display?

---

### Post by Delliriumy on 2014-07-12
Problem solved...i think. It all came down to regenerate xorg.conf and restart few times lightdm then restart pc.

---


---
title: "Ubuntu 22.04 freezes on boot"
date: 2023-12-07
forum: Installation &amp; Upgrades
---

### Post by acromano on 2023-12-07
I installed Ubuntu 22.04 on a Congatec MA7 board (Elkhart Lake). It sometimes gets stuck booting always at the same location. 
Any assistance on how to debug the boot process would be appreciated. This is all I get.


[ 0.764702] platform eisa.0: Cannot allocate resource for EISA slot 1
[ 0.764705] platform eisa.0: Cannot allocate resource for EISA slot 2
[ 0.7647091 platform eisa.0: Cannot allocate resource for EISA slot 3
[ 0.764712] platform eisa.0: Cannot allocate resource for Elsa slot 4
 [ 0.764716] platform eisa.0: Cannot allocate resource for EISA slot 5
[0.764719] platform eisa.0: Cannot allocate resource for EISA slot 6 
[0.7647221 platform eisa.0: Cannot allocate resource for EISA slot 7
[0.764726] platform eisa.0: Cannot allocate resource for EISA slot 8
[0.764729] platform eisa.0: EISA: Detected O cards [
[0.764735] intel_pstate: Intel P-state driver initializing
[0.765016] intel_pstate: HWP enabled
[0.765084] ledtrig-cpu: registered to indicate activity on CPUs
[0.765111] efifb: probing for efifb
[0.765134] efifb: No BGRT, not showing boot graphics
[0.765136] efifb: framebuffer at 0x4000000000, using 1200k, total 1200k 0.765139] efifb: mode is 640×480×32, linelength=2560, pages=1
[ 0.765142] efifb: scrolling: redraw
[ 0.765144] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[ 0.765235] Console: switching to colour frame buffer device 80x30
[0.765556] fb0: EFI VGA frame buffer device
[0.765647] resource: resource sanity check: requesting [mem 0x00000000fdfff7 5c-0x00000000fe00175b], which spans more than pnp 00:04 [mem 0xfd6f0000-0xfdffffff]
[0.765677] caller pmc_core_probe+0xdc/0x230 mapping multiple BARS [ 0.766095] intel_pmc_core INT33A1:00: Assuming a default substate order for this platform
[0.766570] intel_pmc_core INT33A1:00: initialized
[0.766940] drop_monitor: Initializing network drop monitor service
[0.781360] NET: Registered PF_INET6 protocol family

---

### Post by yancek on 2023-12-08
How long have you had 22.04 installed on this computer?  Was it working properly for some time?  Did you make any major changes to software/hardware, particularly to any configuration files?  If so, what were they?  What does sometimes mean, once a week, once a month, alternate days?

---

### Post by acromano on 2023-12-15
[COLOR=#000000]Congatec MA7 is a SOM module (s[/COLOR][COLOR=#333333][FONT=&quot]mall form factor computer-on-module (COM) [/FONT][/COLOR])[COLOR=#000000]. SOM modules plug in to a carrier board which is just a motherboard that breaks out the I/O. Ubuntu was loaded on a SOM in a carrier with an HDMI display and then moved to a carrier with a flat panel display. Once moved it never gets past the point above. I am trying to understand where it stops in the boot process. Tried GRUB debugging commands but no helpful info generated.[/COLOR]

---

### Post by MAFoElffen on 2023-12-16
Is this with Ubuntu 22.04 Desktop or Server? The boot messages shown in Post #1 imply it's trying to initialize drivers in the graphics layer... So I am guessing Desktop?

What is the resolution of the flat panel display? You said yuo changed from HDMI to a flat panel display... For LVDS, it's max res is 1280x1024 @ 60 Hz...

Do you get to the Grub2 menu before that? Have you tried to edit the boot line to replace "quite splash" with "-- 3" to see if it comes up with a console prompt?

---


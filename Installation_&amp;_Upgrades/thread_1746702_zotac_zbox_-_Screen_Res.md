---
title: "zotac zbox - Screen Res"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by spegru on 2011-05-02
Hi I just got a Zotac Zbox sd-id12 and been trying to install both Ubuntu 11.04 and Mint10 on it.
Same problem on both: Max screen resolution is 800x600

The graphics chip is apparently Intel GMA 3150

Any ideas?

---

### Post by spegru on 2011-05-04
bump

---

### Post by spegru on 2011-05-05
bump

---

### Post by lykwydchykyn on 2011-05-05
Post the output from this command to see what driver it's using:

```

grep -i driver /var/log/Xorg.0.log

```

Sounds like it's defaulting to the VESA driver.

---

### Post by spegru on 2011-05-10
Thanks. In fact I have an improvement simply buy using the HDMI connection.
Resoultion is now 1280x720 but it still doesn't look quite right

the command output is as below

[    18.500] 	X.Org Video Driver: 8.0
[    18.500] 	X.Org XInput driver : 11.0
[    18.551] (==) Matched intel as autoconfigured driver 0
[    18.551] (==) Matched vesa as autoconfigured driver 1
[    18.551] (==) Matched fbdev as autoconfigured driver 2
[    18.551] (==) Assigned the driver to the xf86ConfigLayout
[    18.552] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.552] 	Module class: X.Org Video Driver
[    18.553] 	ABI class: X.Org Video Driver, version 8.0
[    18.553] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.554] 	Module class: X.Org Video Driver
[    18.554] 	ABI class: X.Org Video Driver, version 8.0
[    18.554] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.555] 	ABI class: X.Org Video Driver, version 8.0
[    18.555] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[    18.557] (II) VESA: driver for VESA chipsets: vesa
[    18.557] (II) FBDEV: driver for framebuffer: fbdev
[    18.558] 	ABI class: X.Org Video Driver, version 8.0
[    18.655] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.656] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.656] (II) intel(0): [DRI2]   DRI driver: i915
[    18.656] (II) UXA(0): Driver registered support for the following operations:
[    18.813] 	Module class: X.Org XInput Driver
[    18.813] 	ABI class: X.Org XInput driver, version 11.0
[    18.956] (II) No input driver/identifier specified (ignoring)
[  2250.566] (II) No input driver/identifier specified (ignoring)
[  2252.210] (II) No input driver/identifier specified (ignoring)

---

### Post by lykwydchykyn on 2011-05-10
Well, looks like it's grabbing the intel driver after all.  Hmmm.

---

### Post by spegru on 2011-05-18
I just did an experiment to see if another PC could pick out the correct resolution. for this screen. It worked Ok and correct resolution seems to be 1360x768, rather than the 1280x720 that I am otherwise stuck with with the Zotac.

Another interesting thing happened was that if I connect via VGA connector it can pick the correct res even on this Zotac box!

However this seems to be related to a thing that others in the forums have seen with this Intel chipset whereby the box in screen settings for screen mirroring is ticked by default - because it only corrected when I unticked it and thereby separated the 'Laptop' screen that is shown by default from the one I am really using. 
It's not a laptop though and there is no other screen!

However unfortunately when I connect via HDMI again it goes back to default and sees only the 'Laptop' screen (which isn't even there!) with the wrong res
Seems like a bug to me....

---

### Post by spegru on 2011-05-19
hmm, I forgot that I  previously only had 800*600  when on VGA. I wonder what changed.
However it looks like this is a combination bug whereby default multiscreen serting is 'mirrored', but with an imaginary 'laptop' screen that forces a lowest common denominator setting AND a failure to detect external screens properly, at least with HDMI.

---


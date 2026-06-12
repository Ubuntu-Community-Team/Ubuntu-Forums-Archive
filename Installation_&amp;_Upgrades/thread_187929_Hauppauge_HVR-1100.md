---
title: "Hauppauge HVR-1100"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by the_plumber on 2006-06-03
I've got a Hauppauge HVR-1100 in the same chassis as a Nova-T. Both work fine under MythTV, but only since I upgraded the kernel to 2.6.16 (as described in a howto on these forums). The HVR-1100 is only recognised under 2.6.16 as far as I can tell, even Dapper Drake (2.6.15, I think?) doesn't seem to like the 1100, but its sweet as a nut under 2.6.16

OK so MythTV works now, but LIRC (when installed via Synaptic) does nearly nothing; all that works are the cursor keys (from a standard 45-key hauppauge remote) when working with the sensor connected to the socket on the back of the Nova-T, while a USB "beanbag" IR receiver just does nothing at all.

I looked round the LIRC site, and downloaded the latest (0.8 ) and tried to compile, but after a successful configure, the "make" fails.

I googled some more, and apparently this is a known problem and there is a patch for LIRC 0.8 to make it compile cleanly under 2.6.16, but there's two problems: 1) I don't know where to find the patch and 2) if I found the patch, I would need some help regarding how to use it; the only time I have patched before was under the control of the HOWTO to get the kernel to 2.6.16.

So, if anyone out there can tell me where I can get the patch, and what to do with it (command-by-command instructions, please, I'm no guru in this area!), I reckon I may be able to get this box to run...

Thanks

The_Plumber

---


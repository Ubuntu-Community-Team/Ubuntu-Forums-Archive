---
title: "Installer crashes when trying to dual boot 16.04.1 with Win10"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by jhind on 2016-08-17
Complete Linux noob here, so be gentle.  I've searched all over the web trying to find a solution to this, but I haven't been able to find anyone with my exact problem so I'm coming here as a last resort.  I'm trying to dual-boot Ubuntu with Windows 10, but the Ubuntu installer keeps freezing and then kicking me back into Windows before I can even start the installation.

I downloaded the most current iso (checksum passed) and put it onto a USB, shrank my partition using Windows disk management to create unallocated space for Ubuntu to use, and then boot from the USB I created.  I get a black screen with this text:
```
[11.843310] nouveau 0000:02:00.0: unknown chipset (120080a1)
[11.843362] nouveau 0000:01:00.0: unknown chipset (120080a1)
[12.382062] usbhid 5-1:1.2: couldn't find an input interrupt endpoint
[13.476532] sd 8:0:0:0: [sde] No Caching mode page found
[13.476550] sd 8:0:0:0: [sde] Assuming drive cache: write through
[22.439336] hid-generic 0003:1B1C:1B20.0002: usb_submit_urb(ctrl) failed: -1
[22.839350] hid-generic 0003:1B1C:1B1E.0004: usb_submit_urb(ctrl) failed: -1
[22.895123] usbhid 5-2:1.2: couldn't find an input interrupt endpoint
[32.097694] EDAC sbridge: ECC is disabled. Aborting
[32.097709] EDAC sbridge: Couldn't find mci handler
``` After a few seconds the code disappears and the Ubuntu installer launches, at which point it eventually freezes up and kicks me back to windows.  Sometimes it freezes at the partitioner; sometimes it freezes at "Who Are You?"; one time it even got to the actual installation part.  But every time it inevitably freezes up for 15-20 seconds  before eventually rebooting into Windows.

I've tried using the option to "Run Ubuntu without installing" and am able to do so, but it still freezes when I launch the installer or partitioner.  I'm thinking the problem must have something to do with those messages from the black screen, but I don't know enough about Linux to do anything about it and searching each of them individually doesn't really give me much more to go on.

For reference, my hardware is:
5960x
Rampage V Extreme
Samsung 950 Pro SSD
2x 980ti

I have a Corsair Strafe keyboard and a Scimitar mouse, which I believe are giving the usb_submit errors, but I don't think that's causing the reboot, is it?

---


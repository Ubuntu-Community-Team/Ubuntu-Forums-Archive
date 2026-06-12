---
title: "No errors, but a display problem and post-login &quot;crash&quot; after clean, fresh install"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by sean56a on 2011-02-03
Saviors, saints, hello,

I've got this older mid-to-low range [Gateway laptop]("http://support.gateway.com/s/Mobile/Q106/MagicLC/1009130sp2.shtml") (integrated graphics, 512MB RAM) that I installed Kubuntu on this evening. It has a brand new hard drive that I formatted this morning using fdisk and mkfs, while running Lucid Puppy Linux off a flash drive.

I wasn't able to use the normal install disk because of display issues--it appeared that the resolution was set incorrectly, so that the dialog box was half obscured at the bottom right of the screen. I used the command-line disk and was able to successfully install Kubuntu.

Now, however, at the login screen, the display still is askew, so that the login dialog is so far to the bottom right that I am not able to see the pop-up menus. I am able to login, however, but only briefly. Between 3-10 seconds after I hit "enter" the screen flashes and I'm back at the login dialog. Again, and over again I may login, and the desktop just starts to resolve (4-5 cute little icons, with lovely, Mac-esque shadows: a hard drive, a "settings" icon... etc).

So tantalizing! ;) Thanks so much for your time. I'm looking forward to becoming a Linux user, and Kubuntu seemed like a good place to start. Cheers!

Sean

---

### Post by matt_symes on 2011-02-03
Hi

Sounds like X is crashing. Use puppy to look at the logs in /var/log after mounting the drive

```
less <mount point>/var/log/Xorg.0.log
```

What is your graphics card ?

Kubuntu with KDE might be too heavy for your system.

Kind regards.

---

### Post by sean56a on 2011-02-03
Thanks Matt,

I looked at the log, but it's a bit too cryptic for me. Attached (change the file extension back to .log). The graphics are reported by the Gateway website (the "Gateway laptop" text in the above post is a link to it) as: 

S3 UniChrome&#8482; Pro integrated graphics - Up to 64 MB shared video memory

If you don't think I can run Kubuntu, can you recommend another distro that is as user-friendly? Perhaps the regular Ubuntu?

Thanks,

Sean

---

### Post by matt_symes on 2011-02-03
Hi

Well, this is the pertinent part of the log file you posted.

```
[    48.144] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.144] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    48.145] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    48.145] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    48.145] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    48.145] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    48.145] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    48.145] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.145] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    48.145] (II) No input driver/identifier specified (ignoring)
[    66.505] (II) Power Button: Close
[    66.505] (II) UnloadModule: "evdev"
[    66.505] (II) Video Bus: Close
[    66.505] (II) UnloadModule: "evdev"
[    66.505] (II) Power Button: Close
[    66.505] (II) UnloadModule: "evdev"
[    66.505] (II) Sleep Button: Close
[    66.505] (II) UnloadModule: "evdev"
[    66.507] (II) Logitech USB Laser Mouse: Close
[    66.507] (II) UnloadModule: "evdev"
[    66.507] (II) AT Translated Set 2 keyboard: Close
[    66.507] (II) UnloadModule: "evdev"
[    66.507] (II) UnloadModule: "synaptics"
[    66.569] (II) CHROME(0): VIACloseScreen
[    66.580] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[    66.584] (II) CHROME(0): [drm] Freeing agp memory
[    66.588] (II) CHROME(0): [drm] Releasing agp module
[    66.588] (II) CHROME(0): [drm] removed 1 reserved context for kernel
[    66.588] (II) CHROME(0): [drm] unmapping 8192 bytes of SAREA 0xdc6b9000 at 0xb7806000
[    66.588] (II) CHROME(0): [drm] Closed DRM master.
[    66.588] Freed 30726400 (pool 1)
[    66.588] (II) CHROME(0): [drm] IRQ handler uninstalled.
[    66.588] (II) CHROME(0): VIARestore
[    66.589] (II) CHROME(0): ViaLCDPower: On.
[    66.589] (II) CHROME(0): ViaDisablePrimaryFIFO
[    66.589] (II) CHROME(0): VIAUnmapMem
[    66.599]  ddxSigGiveUp: Closing log
```

As you can see at 48.145 all is well, then there is a gap and at 66.505 everything starts shutting down with no explanation as to why. Don't you just love that ?

We might be able to glean more information from some of the other logs. Can you get the logs...

```
/var/log/syslog
/var/log/messages
/var/log/kern.log
```

I am not sure if your grahpics card can handle KDE and you don't have much memory but others might know for definite. In the meantime post the new logs.

There might be a number of better options for you than kubuntu.

Kind regards

---

### Post by sean56a on 2011-02-03
Okay, so while everything was going haywire, the log failed to write? This is like the Nixon tapes! I've attached the three you requested, again appending the filenames with .doc for the upload. Cheers.

Sean

P.S. I actually don't have a separate graphics card, it's onboard motherboard graphics. So, really, really bad.

---

### Post by sean56a on 2011-02-04
Could anyone offer some alternatives to Kubuntu? Should I try Ubuntu?

---


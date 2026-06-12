---
title: "PPC - Xserver  issues on installing Karmic"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frog_pilot on 2009-09-26
After installing karmic on my ibook g4/800 MHz, ATI Radeon Mobility 9200 32 MB AGP there was first an xserver-problem. the video-card started in framebuffer mode with 256 colors.

After installing libdrm-radeon1 manually according to [this bugreport]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/434894"), it works.

But there is still an issue with tehe video-ROM on starting up. After Display-Detection I get this message
```
Sep 25 16:20:27 punkbook kernel: [    0.840650] radeonfb 0000:00:10.0: Invalid ROM contents
Sep 25 16:20:27 punkbook kernel: [    0.840675] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55

```
And xorg.0.log shows this
```
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9200 (M9+) 5C63 (AGP)" (ChipID = 0x5c63)
(--) RADEON(0): Linear framebuffer at 0x0000000098000000
(II) RADEON(0): AGP card detected
(WW) RADEON(0): Failed to read PCI ROM!
(II) RADEON(0): Attempting to read un-POSTed bios
(WW) RADEON(0): Failed to read PCI ROM!
(WW) RADEON(0): Unrecognized BIOS signature, BIOS data will not be used

```
After this ubuntu continues starting up. I can't see any Problems besides the System is unable to shut down properly.

Would it be better to prevent the module fbdev from being loaded?
In earlier Version the PCI-Bios thing was an issue and there was an Option-String for the device-stanza in xorg.conf. But where can I put this now in an xserver without xorg.conf?
```
Option "NoInt10" "yes"
```

There is another issue with the keyboard layout. I selected ALT as "Key to choose 3rd Level". Now I can get @ as usual with ALT+L, but ALT+F2 for the run-menu isn't working and this is an important feature for me.

Is there a way to create a right-click with the mouse-pad?

Suspend isn't working at all. But I remember this was an issue of every ppc-release...

Thanks in advance for any response!

---


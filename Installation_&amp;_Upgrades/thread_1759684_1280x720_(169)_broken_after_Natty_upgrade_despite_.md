---
title: "1280x720 (16:9) broken after Natty upgrade despite proper modelines"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by grumpypants on 2011-05-16
I have a Samsung 22" LCD TV whose native resolution is 1280x720. I've been driving it with G965 Intel chipset graphics since Feisty Fawn. After upgrading to Natty, I see a cropped and scaled screen. Basically it's like a frame wide enough to include the menu bar and half the launcher has been cropped off and then the monitor has scaled the remaining piece to fill the screen. What's weird is:
 • If I set a lower resolution it works fine and nothing is cropped. None of the lower resolutions are 16:9; not sure if relevant.
 • If I connect a different screen everything works fine at 1280x960, 1920x1200. (1280x720 not available on this monitor).
 • If I connect the 22" LCD TV to another computer (Macbook) it still works fine at 1280x720.

I've gone through the /var/log/Xorg.logs and not much has changed. The differences I noticed, other than ordering of the log lines, were:

Maverick: (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
Natty: (II) intel(0): Kernel page flipping support detected, enabling

Natty only: (**) intel(0): Relaxed fencing enabled

Potentially interesting lines that are the same in Maverick & Natty:
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965G
(--) intel(0): Chipset: "965G"
(**) intel(0): Relaxed fencing enabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled

(==) Depth 24 pixmap format is 32 bpp
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): [DRI2] Setup complete
(II) intel(0): [DRI2]   DRI driver: i965
(II) intel(0): Allocated new frame buffer 1728x1050 stride 7168, tiled
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(II)         get_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): [XvMC] i965_xvmc driver initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(==) intel(0): hotplug detection: "enabled"
(--) RandR disabled

(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_INTEL_swap_event
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 190
(II) intel(0): Allocated new frame buffer 1280x720 stride 5120, tiled

(II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1350 1390 1650  720 725 730 750 -hsync +vsync (45.0 kHz)

Cheers!

---


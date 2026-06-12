---
title: "OpenGL not working / lubuntu 13.10 / Radeon X600 / iMac G5 revC"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by tigheron on 2013-10-26
I just upgraded my aging iMac G5 revC from lubuntu 13.04 to lubuntu 13.10.

The good news is that (almost) everything went fine. I am currently writing from the computer :p
 Unfortunately, I met two problems:
1) a kernel panic during the upgrade of the apparmor stuff (which I then disabled), but I solved that issue.
2) OpenGL support is gone.

When I try to run glxinfo, I get the following error:

$ LIBGL_DEBUG=verbose glxinfo
name of display: :0
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/tls/r300_dri.so
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/r300_dri.so
libGL error: failed to load driver: r300
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x064  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
[snip]

And none of the opengl-based programs work (they did reasonably well under 13.04).

Needless to say, but /usr/lib/powerpc-linux-gnu/dri/r300_dri.so is there, and I have the permissions to read and execute the file.
Also, all the shared libraries that are referenced from r300_dri.so are installed and visible

> 
$ ldd /usr/lib/powerpc-linux-gnu/dri/r300_dri.so
        linux-vdso32.so.1 =>  (0x00100000)
        libdricore9.2.1.so.1 => /usr/lib/powerpc-linux-gnu/libdricore9.2.1.so.1 (0x6fb1b000)
        libgallium.so.0 => /usr/lib/powerpc-linux-gnu/libgallium.so.0 (0x6f71a000)
        libdrm.so.2 => /usr/lib/powerpc-linux-gnu/libdrm.so.2 (0x6f6ee000)
        libexpat.so.1 => /lib/powerpc-linux-gnu/libexpat.so.1 (0x6f69f000)
        libpthread.so.0 => /lib/powerpc-linux-gnu/libpthread.so.0 (0x6f664000)
        libdrm_radeon.so.1 => /usr/lib/powerpc-linux-gnu/libdrm_radeon.so.1 (0x6f637000)
        libm.so.6 => /lib/powerpc-linux-gnu/libm.so.6 (0x6f567000)
        libc.so.6 => /lib/powerpc-linux-gnu/libc.so.6 (0x6f3ca000)
        libgcc_s.so.1 => /lib/powerpc-linux-gnu/libgcc_s.so.1 (0x6f393000)
        libglapi.so.0 => /usr/lib/powerpc-linux-gnu/libglapi.so.0 (0x6f33b000)
        libstdc++.so.6 => /usr/lib/powerpc-linux-gnu/libstdc++.so.6 (0x6f1ea000)
        libLLVM-3.3.so.1 => /usr/lib/powerpc-linux-gnu/libLLVM-3.3.so.1 (0x6db12000)
        libdl.so.2 => /lib/powerpc-linux-gnu/libdl.so.2 (0x6daee000)
        /lib/ld.so.1 (0x201b3000)
        libffi.so.6 => /usr/lib/powerpc-linux-gnu/libffi.so.6 (0x6dac5000)


I tried reinstalling mesa, even from source, but still I can't figure out what is happening, let alone how to fix it.

Any idea, suggestion, (or question)?
I am attaching the output of "dmesg | grep -i radeon" and the Xorg.log file below, just in case you want to take a look.

Thx in advance ;)

--- dmesg | grep -i radeon ---
[    0.000000] Kernel command line: root=UUID=32e4a5f6-3a5d-4788-b14f-f89ecb3a128d ro video=radeonfb:off radeon.modeset=1 video=1920x1080-32 nosplash 
[   30.161243] [drm] radeon kernel modesetting enabled.
[   30.161432] fb: conflicting fb hw usage radeondrmfb vs OFfb ATY,Aphrod - removing generic driver
[   30.280781] fb: conflicting fb hw usage radeondrmfb vs OFfb ATY,Aphrod - removing generic driver
[   30.336283] radeon 0000:04:00.0: enabling device (0006 -> 0007)
[   30.380753] radeon 0000:04:00.0: Using 64-bit DMA iommu bypass
[   30.380976] radeon 0000:04:00.0: Invalid ROM contents
[   30.381048] radeon 0000:04:00.0: Invalid ROM contents
[   30.381076] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[   30.381204] radeon 0000:04:00.0: VRAM: 128M 0x0000000098000000 - 0x000000009FFFFFFF (128M used)
[   30.381214] radeon 0000:04:00.0: GTT: 512M 0x0000000078000000 - 0x0000000097FFFFFF
[   30.390844] [drm] radeon: 128M of VRAM memory ready
[   30.390854] [drm] radeon: 512M of GTT memory ready.
[   30.436766] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   30.514014] radeon 0000:04:00.0: WB enabled
[   30.514065] radeon 0000:04:00.0: fence driver on ring 0 use gpu addr 0x0000000078000000 and cpu addr 0xc00000000df4a000
[   30.514532] [drm] radeon: irq initialized.
[   30.841117] [drm] radeon: ring at 0x0000000078001000
[   30.943276] [drm] Radeon Display Connectors
[   34.869687] radeon 0000:04:00.0: fb0: radeondrmfb frame buffer device
[   34.869696] radeon 0000:04:00.0: registered panic notifier
[   34.897480] [drm] Initialized radeon 2.34.0 20080528 for 0000:04:00.0 on minor 0
--- end of dmesg ---

[ATTACH]247251[/ATTACH]

---

### Post by tigheron on 2014-02-08
Dear 25 worldwide users of Ubuntu 13.10 on the iMac G5, ):P

I found that the "hack" suggested [in this post]("https://lists.debian.org/debian-powerpc/2013/12/msg00044.html") does work for me.
Just rename /usr/lib/powerpc-linux-gnu/dri/r300_dri.so, restart the X-server (e.g. by logging out and in) and things will (hopefully) work.

Rejoice!\\:D/

---


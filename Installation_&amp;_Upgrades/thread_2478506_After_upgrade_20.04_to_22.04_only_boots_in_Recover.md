---
title: "After upgrade 20.04 to 22.04 only boots in Recovery mode. Resolution stuck at 800x600"
date: 2022-08-28
forum: Installation &amp; Upgrades
---

### Post by CapnWhizBang on 2022-08-28
I have an older HP running motherboard aahd3-hb.
[http://www.ascendtech.us/hp-aahd3-hb-motherboard-655590-001_i_mbhpaahd3hbhibi.aspx](http://www.ascendtech.us/hp-aahd3-hb-motherboard-655590-001_i_mbhpaahd3hbhibi.aspx)
It appears that there is now a problem with the driver it tries to load for the built in Radeon HD 6550D graphics hardware. Trying to boot it normally ends with "no signal" on the monitor. It will boot in "Recovery" but it is then in 800x600 resolution.
I found someone with the same symptom [but probably a different board] that suggested updating the line in grub to have "radeon.modeset=0" in it. That didn't help me.

"glxinfo -B" and "xrandr" output can be seen after my closing questions.

It seems that what is really needed is an updated driver for the radeon hardware. Not sure if/when that might become available. So I am looking for alternative solutions.

1. Is there a way to get the current recovery mode renderer to render in anything other than 800x600? 
2. Can I just buy a very cheap video card and throw that in?

name of display: :1
display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa/X.org (0xffffffff)
    Device: llvmpipe (LLVM 13.0.1, 128 bits) (0xffffffff)
    Version: 22.0.5
    Accelerated: no
    Video memory: 13466MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Mesa/X.org
OpenGL renderer string: llvmpipe (LLVM 13.0.1, 128 bits)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 22.0.5
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.5 (Compatibility Profile) Mesa 22.0.5
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20



xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600       75.00*

---


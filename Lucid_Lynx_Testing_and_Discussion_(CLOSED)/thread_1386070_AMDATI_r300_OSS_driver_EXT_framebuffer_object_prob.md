---
title: "AMD/ATI r300 OSS driver: EXT_framebuffer_object problem"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by barisurum on 2010-01-20
Hello all fellow testers;

I try to run a fbo demo but it gives me this:

```
Video card supports GL_EXT_framebuffer_object.
Allocating 256 x 256 radeon RBO (pitch 256)

***** FBO STATUS *****
Max Number of Color Buffer Attachment Points: 8
Color Attachment 0: GL_TEXTURE, 256x256, GL_RGBA8
Depth Attachment: GL_RENDERBUFFER_EXT, 256x256, GL_DEPTH_COMPONENT

Framebuffer complete.
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
```

dmesg says:

> [  718.778530] [drm:r100_cs_track_check] *ERROR* [drm] No buffer for z buffer !
[  718.778536] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 1078.394280] [drm:r100_cs_track_check] *ERROR* [drm] No buffer for z buffer !
[ 1078.394285] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 1098.658073] [drm:r100_cs_track_check] *ERROR* [drm] No buffer for z buffer !
[ 1098.658078] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

but my card is an r500! What the heck about this r100? Anyone having the same issue?

---

### Post by MadMan2k on 2010-01-20
the r300 driver is quite buggy and not really maintained any more. Try r300g (the gallium driver). It is also still buggy - but less ;)

---

### Post by barisurum on 2010-01-20
Can you give me (and others) instructions how to do that? My card is an X1650XT

---

### Post by clhsharky on 2010-01-20
HI barisurum

I have a ATIX1650 card with KMS/DRI2 activated, the r300 OSS driver
has been stable for me. The gallium driver was very slow.

 Lots of info at Phoronix Open-Source AMD/ATI Linux
[http://www.phoronix.com/forums/forumdisplay.php?f=43](http://www.phoronix.com/forums/forumdisplay.php?f=43) 

Sharky

---


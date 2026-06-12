---
title: "after update upgrade,  video 4 linux 2 is broken?"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-09-27
just did an update upgrade and can no longer stream capture thru VLC

> Your input can't be opened:
VLC is unable to open the MRL 'v4l2://'. Check the log for details.

> scott@scott-desktop:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x8206688] main interface error: no interface module matched "globalhotkeys,none"
[0x8206688] main interface error: no suitable interface module
[0x8166140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8166140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x84a3d40] v4l2 demux error: device does not support streaming i/o
[0x84a3d40] v4l2 demux error: cannot get video input characteristics (Invalid argument)
[0x848e078] v4l2 access error: device does not support streaming i/o
[0x848e078] v4l2 access error: cannot get video input characteristics (Invalid argument)
[0x84a1d28] main input error: open of `v4l2://' failed: (null)


well, the problem was not v4linux2 but with VLC 1.0.2
vlc 1.0.0 works fine.

---


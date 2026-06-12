---
title: "Seeking a bit of adivce re jerky DVD playback"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-19
Last night I managed to get DVD playback enabled so I can watch movies on my box. However, I noticed a bit of jerky behavior during the movie playback and upon further research I found this in the Wiki [DMA](https://wiki.ubuntu.com/DMA).

Investigating my DVD drive with hdparm returns this info:

> 
/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


As can be seen, DMA is not enabled. So I've two questions:

1) In light of the big bolded warning at the top of the DMA page (see link) I'm a bit nervous about trying this, so should I proceed with the instructions? The playback is definitely not that bad. It's watchable, and I only notice the jerky behavior when the camera pans or there's a lot of action (and even then, it's not horrible), but I'd like to correct it if possible.

2) What does the "HDIO_GETGEO failed: Invalid argument" message mean?

Thanks for any help.

---

### Post by darkpark on 2006-02-19
Go ahead and enable DMA mode.  i have not had a single problem using DMA mode.  Also, I enabled multisector read which helps improve reading speed.

---

### Post by Coelocanth on 2006-02-19
Thanks Dark. Any thoughts on editing the hdparm.config file? I can always re-enable DMA upon boot-up, but it would be nice to have it automatic. Not sure I'm comfortable editing the file though. Meh, maybe I'll just do it...

---


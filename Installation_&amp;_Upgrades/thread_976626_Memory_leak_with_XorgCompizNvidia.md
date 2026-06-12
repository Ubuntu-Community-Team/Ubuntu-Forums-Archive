---
title: "Memory leak with Xorg/Compiz/Nvidia?"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by der.mikus on 2008-11-09
I just got done upgrading Hardy 64-bit to Ibex 64-bit hoping to fix a memory leak that I could never trace down to any one app, and doing so just seems to have exacerbated the issue. crapola.  I'm hoping that someone else might be able to divine a clue as to what is going on, or point me toward figuring it out.

Thus far I've had this leak now on Feisty, Gutsy, Hardy, and Ibex, whereas on Feisty I was using Kubuntu, and have been using Ubuntu w/Compiz since Gutsy.  KDE has always had it's own issues, so who knows what was broken back in Feisty, but the memory leak from Gutsy on always seems related to Xorg, Compiz, or something having to do with the Nvidia card, as it's really the only commonality that isn't 100% obvious.

When running the "free" command, I can always see my memory slowly going to nothing over time, though gkrellm always shows that I have a high amount of "free" memory.  I really can't explain why there is a disparity here (advice is welcome).  Trying to diagnose what is causing the leak, I'd researched that said watching top and ctrl-m to sort by memory only ever shows Xorg and compiz.real to be the worst offenders, though I still never see them go over 1-2%, if even that as a peak.  Nothing else ever shows significant use of the memory or cpu, but still I see my free memory going down via "free", and still gkrellm still says I have most of my 8gb of memory free.  Who can I trust here?

The symptoms typically I'd notice that memory is leaking to nill is that after some time I'll have a bunch of firefox windows open, and then I'll try to watch a video via VLC for example.  When launching VLC, the window will just exit immediately when trying to render the window.  I can killall the firefox processes, then I can launch VLC.  Most other apps tend to work fine in this situation, with no real discernible problem.  This tends to lead me to believe there may be something with Xorg or the Nvidia drivers.

On ibex now I'm running the 177 glx drivers in a twinview config on 2 monitors, and thus far I'm seeing the exact same symptoms, though after upgrading 20 other things are broken to, so I really don't even know where to begin.  I've done just about everything I know how to diagnose the matter unsuccessfully short of migrating to ATI hardware.  Anyone have similar experiences and/or resolutions?  

Thanks in advance!

-mb

---


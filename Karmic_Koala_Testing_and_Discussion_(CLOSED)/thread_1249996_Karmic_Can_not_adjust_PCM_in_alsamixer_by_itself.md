---
title: "Karmic: Can not adjust PCM in alsamixer by itself"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MikePontillo on 2009-08-26
After upgrading from Jaunty to Karmic, I am seeing a new problem with sound. It has worked fine on this machine for several Ubuntu releases, except that I always had to use 'alsamixer' to turn down the "PCM" volume. On my particular system (a laptop) if I leave "PCM" turned up all the way, (the default) my speakers sound terrible. In the past I have just turned it down a little, and used "Master" to adjust the volume.

A new feature in Karmic is, when I launch alsamixer and try to adjust "PCM", (turn it down) it adjusts "Master" instead. Of course, this ruins everything for me.

I'm pretty sure it's pulseaudio that's doing this. I found forum threads from the distant past that suggested that I should adjust the mixer settings, then run "alsactl store 0" to save them. So I set out to try to do that, keeping in mind that I had to shut down pulseaudio first, otherwise I wouldn't be able to set up the mixer correctly.

The first problem I had doing this was, I can't shut down pulseaudio! I tried its "--kill" option, which seems to kill it and then restart it again right away. (though I'm not sure what's restarting it - from "ps -ef" it looks like /sbin/init, but I can't use "/sbin/init.d/pulseaudio stop" because it errors out saying it's configured for per-user sessions)

So I took the brute force approach, set "chmod -x /usr/bin/pulseaudio", killed the process, and saved my mixer settings with alsactl. But it didn't work - as soon as I made pulseadio executable again, it restarted itself and set my PCM volume back to 100%.

Next I suppose I'll dig through all the pulseaudio settings, and see what changed from Jaunty. But I'm hoping someone already knows where to look... any ideas?

**Update:**
I have filed bug [420578]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420578") on this issue.

---


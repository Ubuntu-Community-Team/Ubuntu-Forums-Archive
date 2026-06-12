---
title: "What's the deal with the new mixer?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by H3g3m0n on 2009-09-25
By default the sound comes out with this incredible high pitched tinny sound. Took me a little while to realize the problem since it was just about on the edge of my hearing range, it was like dragging nail across a chalk board in my subconscious, although it made the quality overall terrible too.

If I lower the PCM to around 50 and set the Master to 100 then it sounds fine.

The problem is there doesn't seem to be any way to change the default mixer channel, so every time I adjust the volume the Master changes instead and the PCM jumps to 100.

I want the default mixer to be PCM rather than Master. Under 9.04 there was the Sound option in preferences but under 9.10 its a different dialog.

I have also noticed that the mixer likes to adjust the Front/Surround/whatever channels when I change the PCM instead of just changing the PCM.

There also doesn't seem to be an option to change between Pulse/Alsa/OSS anymore. This isn't such an issue since Pulse now seems to actually work (other than the mixer), but it could be a major problem for anyone with issues with pulse. There is also no way to manually change the channels other than jumping to alsamixer, or some other mixer, other than the Master/mic channels meaning there is no way to adjust the level of surround sound speakers.

---

### Post by hanzomon4 on 2009-09-25
> **H3g3m0n said:**
> By default the sound comes out with this incredible high pitched tinny sound. Took me a little while to realize the problem since it was just about on the edge of my hearing range, it was like dragging nail across a chalk board in my subconscious, although it made the quality overall terrible too.

If I lower the PCM to around 50 and set the Master to 100 then it sounds fine.

The problem is there doesn't seem to be any way to change the default mixer channel, so every time I adjust the volume the Master changes instead and the PCM jumps to 100.

I want the default mixer to be PCM rather than Master. Under 9.04 there was the Sound option in preferences but under 9.10 its a different dialog.

I have also noticed that the mixer likes to adjust the Front/Surround/whatever channels when I change the PCM instead of just changing the PCM.

There also doesn't seem to be an option to change between Pulse/Alsa/OSS anymore. This isn't such an issue since Pulse now seems to actually work (other than the mixer), but it could be a major problem for anyone with issues with pulse. There is also no way to manually change the channels other than jumping to alsamixer, or some other mixer, other than the Master/mic channels meaning there is no way to adjust the level of surround sound speakers.


That sounds like hell, file a bug

---

### Post by H3g3m0n on 2009-09-25
Oddly enough its not happening anymore. Might have been fixed by nuking the ~/.pulse and ~/.pulse-cookie directories.

Otherwise it might be having Front, Surround and PCM channels are all at %100 (actually the PCM is currently at 99, for some weird reason changing the Master volume using the normal mixer causes it to jump randomly around between 100,98,97 but its not such an issue.). I'm not sure if they where %100 before the Front/Surround might have been around %50.

There are still a bunch of issues with the new mixer for anyone that needs decent control over the mixer settings, still seems to be taking mixer settings from one channel and transferring them to other channels, but there not causing any problems currently.

---

### Post by H3g3m0n on 2009-09-30
Looks like it is happening still.

It seems as soon as I use the gnome mixer app it goes tinny sounding. When I make a change in alsamixer it fixes the problem, even if all I do it turn to volume up then down again to exactly the same state.

It seems the application changing the settings is having some effect on something other than the channel volume.

Doing a bug now...

---


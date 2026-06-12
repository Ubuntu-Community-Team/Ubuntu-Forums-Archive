---
title: "PA does not support multiple streams in karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by waspbr on 2009-10-23
Honestly I hate to have to post about PA, given the reputation that it has. But this has been a real stick in the mud for me. Whenever I have firefox open with something that uses audio, say a flash video, then the sound gets muted for any other sound application namely banshee/songbird/rhythmbox/... 

I have had this problem for a little while now but I kept thinking that is was a temporary woe that would soon be fixed in a later update. Is there any fix for this issue?

---

### Post by rockin_goliath on 2009-10-23
Unfortunately (or fortunately, depending on how you look at it), I do not have the same problem (see the screenshot).

<obvious>
Have you made sure that the streams themselves are not muted in the sound preferences? I noticed that if I turn one of the streams all the way down, the mute button for that stream will turn on, and then not turn off again when I turn the volume of the stream back up. I have to uncheck it manually.
</obvious>

Have you checked to make sure that no essential packages have been removed, possibly by running partial upgrades? Trying the system off the LiveCD (daily builds?) would allow you to better diagnose the problem, since you would be using the stock set of packages and configurations. If the problem goes away, you might be able to just do a clean reinstall. If you still have the problem, it might be the way PulseAudio or ALSA is handling your sound device.

Also, if you do a clean reinstall, backup and remove any custom PulseAudio config files that you might have made in your Home directory.

Please file a bug on the issue and stay on top of the information the Devs ask you to provide!

---

### Post by Joe_Bishop on 2009-10-23
> **waspbr said:**
> Honestly I hate to have to post about PA, given the reputation that it has. But this has been a real stick in the mud for me. Whenever I have firefox open with something that uses audio, say a flash video, then the sound gets muted for any other sound application namely banshee/songbird/rhythmbox/... 

I have had this problem for a little while now but I kept thinking that is was a temporary woe that would soon be fixed in a later update. Is there any fix for this issue?
You need to install pavucontrol to operate with streams. IMHO, the gnome volume control applet makes the whole Pulse Audio idea pointless -- we have the same functionality before with alsa and esd, but without sound glitches and high CPU usage.

---


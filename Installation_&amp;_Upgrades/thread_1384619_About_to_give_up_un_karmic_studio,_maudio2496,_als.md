---
title: "About to give up un karmic studio, maudio2496, alsa."
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by evozero on 2010-01-18
Hi all,
I am having a nightmare with karmic studio, and wanted to know if any one else has had all the same problems.
Fresh install, went very smoothly, booted up no problem.
Load jack,  i got the usual memory limit warnings.
Tried studio controls, doesn't work, found out its a bug.
Manually edited the /etc/sec/limits.conf, working.
Then i get no sound through the maudio2496 ice1712, ok load up envy24 control,thinking the channels would be muted, no joy.
Tried Ardour, sound works, very odd...
Another day of messing around pulling my hair out, find out its another bug
edit the ICE1712.conf, it works!
So by this point i have spent a good few days on this, but think i have finally cracked it...
load LMMS, sound is completely screwed up, out putting garbage via Alsa, ok try jack, i get loads of messages about latency timings and keeps crashing out.
I have tried upgrading alsa, pulse, jackd, added the backports ( then i loose the RT kernel ) you name it!
I know lots of other people are having similar problems, so my question is what should i do next? My config is very basic, AMD2600, 1 gig ram, onboard sound card disabled.
I really want to use UBstudio, especially Ardour, LMMS, and the latest versions if possible, is this asking too much at the moment?
Sorry for the rant, and i am looking for some constructive suggestions.
Thanks
Ian

---


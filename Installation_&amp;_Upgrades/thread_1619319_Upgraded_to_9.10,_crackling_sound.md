---
title: "Upgraded to 9.10, crackling sound"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Sagorn on 2010-11-11
I recently upgraded from 9.04 to 9.10 (9.04 support just ran out).  Ideally, I'd upgrade further to 10.04 or 10.10, but I am somewhat bandwidth limited, and so the additional 1.5GB upgrade to 10.04 is a last resort.

After upgrading, I picked up a nice crackling sound.  It seems to be tied to activity.  Typing up this post resulted in a few crackling sounds a minute, but scrolling up or down, resizing windows, or doing anything more intensive (such as listening to music), and the frequency picks up.

lspci lists two audio devices: 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
Though I believe the second one is for a port on my video card, and thus the first one seems to be the one actually in use.

If it matters at all, I'm running 64-bit, and am currently dual booting with Arch Linux (which has its own audio issues, and I was putting off tracking down because Ubuntu worked fine).

Thank you for any help you can provide.

---

### Post by Sagorn on 2010-11-11
Well, I figured out the root cause, strange as it is.
Apparently my computer case (Antec 300) is set up in a way that is prone to em interference, causing audio static.  Moving headphones to the rear jack (after ensuring that the rear jack is actually active and not muted in Alsa) solved the crackling problem.  

I can't fathom how exactly this problem only surfaced when I upgraded to 9.10, given more than a year of 9.04 with no issues, but I'll take what I can get.

---


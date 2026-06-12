---
title: "sound packed up on eeepc 904HD....I may yet cry :("
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Fenris_rising on 2009-04-05
Hi all

Well seeing as the sound in 8.10 on my eepc packed up and refused to be fixed I chanced my arm with jaunty seeing as the sound did work. Well the emphasis is on DID. It bloody did this afternoon now for no reason at all it doesn't (no updates performed, no suspend to ram or hibernate options have been attempted)

Suddenly it just doesn't make a sound. Well it does but that consists of the login prompt and the login successful sounds. Thereafter it does bugger all. With a lot of poking around I have set everything from autodetect or Alsa to OSS in the gstreamer properties, and Realtek ALC269(OSSmixer) in the volume settings and sound.

This works except the volume slider doesn't control the volume at all, neither does the Fn keys though the graphic acts like they do and in fact the only way to control the volume is with the current applications own volume control.

Can anyone tell me how to sort this properly as I am rapidly approaching the point where I am going to start extracting my teeth. I have had sound problems for at least 3 weeks now with 8.04 (sorted sort of) 8.10 and now jaunty. To be fair jaunty is beta so some trouble has to be expected but it's happening in the 'stable' OS's to and I can't for the life of me ,even with this forum to search find out what the *****y hell is going on.

Whats going on are the creators of the greatest OS in the universe trying to cull the followers by mental abuse???????? Help me please I am going out of my mind #-o

regards

Fenris

---

### Post by jpeddicord on 2009-04-05
> **Fenris_rising said:**
> Suddenly it just doesn't make a sound. Well it does but that consists of the login prompt and the login successful sounds. 

Judging by that line, sound *is* working, but something is blocking it from other applications. Have you done any sound/driver customization lately?

---

### Post by Fenris_rising on 2009-04-06
I have done nothing to anything :( This is exactly the problem I had with easy peasy on my eeepc. Login sounds present but thereafter nothing. Under sound preferences I have set it as follows (back to the Alsa settings)

```
Auto Detect

Auto Detect

Auto Detect

HDA intel ALC269 Anologue (Alsa)

HDA Intel (Alsa mixer)

PCM
Linout
Capture
```

Volume control is set to;

```
HDA Intel (Alsa mixer)
```

PCM and Lineout are at maximum and the volume slider on the desktop at least controls the PCM slider again but no sound at all. Where do I go from here?

EDIT: Well having set everything back up my desktop crashed. I still had my background and pointer and the compiz cube worked but no upper or lower panels. So I rebooted and jaunty restarted. Now it logged in fully under it's own steam (I have it set for password) and the login ready chimed in as well. Back to a working desktop and at this moment all sound now works (though there is a nasty click every now and then). Nothing else has been done other than setting up the Alsa tabs. For future reference has anyone a clue as to what happened?

regards

Fenris

---

### Post by Fenris_rising on 2009-04-06
RIGHT! Jaunty just dropped out again (panels vanished and only compiz cube left) Reboot and the sound has freaked out again...........as in no bloody sound...........

Fenris (irate and likely to fart blood)

---


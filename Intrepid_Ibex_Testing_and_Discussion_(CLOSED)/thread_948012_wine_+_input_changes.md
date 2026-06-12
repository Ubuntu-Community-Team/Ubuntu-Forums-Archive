---
title: "wine + input changes"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xianthax on 2008-10-14
Updated to Ibex beta yesterday and have run into a problem with wine + ventrilo + key detection.  

First of all, this doesn't appear to be the same problem there are already 8,000 threads about, seems to be separate and i can't find a thread discussing it anywhere...

in hardy i was using the wine in the backports rep (1.0.not sure) with ventrilo 3.0.1 without issue, including PTT from within other wine programs working, i.e. without focus of the ventrilo window, as long as the app with focus was run in wine it worked, which is good enough for me...

wine is setup using alsa for audio and i have not had any problems with the audio in any wine apps, even after updating to Ibex.

what i do have a problem with is the PTT key detection in ventilo now.  No matter what window has focus its as if the ventrilo window is not listening for key presses.  which is weird because it does detect the pressing of the key within the setup window.  so selecting the key i want to press to trigger PTT works fine.  however pushing the key does nothing, no matter what app has focus,  key detection in all other wine programs is fine.

more interesting things....if i force wine to use OSS for audio, the PTT key is properly detected, however the audio does not work...its as if, all of a sudden, using alsa for audio in wine is blocking ventrilo from detecting key presses.  

i've tried all permutations of using direct input / direct sound in the ventrilo settings.  i've also tried ventriloctrl to force key events to ventrilo.  neither works.  

its unclear to me where this bug should go, wine? the audio system? etc it looks like ibex has wine 1.0 as well but i'm not sure if there was some minor change in that package or not.

thanks

-x

---

### Post by xianthax on 2008-10-14
further testing reveals what i think is the problem:

audio input appears to be broken...atleast capture....

i didn't look at this at first because i have the mic input played back through the output, i.e. i hear what i say in the mic in my headphones.  this still works as before, so i assumed that input was working....

in testing in the sound recorder and audacity i can't get a mic input and in fact audacity bricks on opening the input device.  

within the volume control applet on the recording tab of alsa, it shows "capture" and "digital" as input sources, the button to enable an input source appears to work, however if I close the volume control applet and reopen it, both are again, unselected.  

i would guess that wine is bricking attempting to open the input source and this causes ventrilo to, in turn, appear to not respond to the input key (even the talking graphic does not appear)...

more digging to follow...

-x

---

### Post by xianthax on 2008-10-14
problem solved....ish?

killall pulseaudio made the input device openable...

for some reason the analog mic input on my laptop is controlled via the digital volume slider on the recording tab of alsa in the volume control applet and the "source selected" button always resets to not selected for both the digital and capture sources on the recording tab when the volume control applet is closed then reopened...

the above bugs appear to have been reported before so i guess this is closed.

-x

---


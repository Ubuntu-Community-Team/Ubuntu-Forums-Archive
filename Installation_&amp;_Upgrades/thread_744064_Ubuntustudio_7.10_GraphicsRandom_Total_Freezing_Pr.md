---
title: "Ubuntustudio 7.10: Graphics/Random Total Freezing Problem"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2008-04-03
I just did a fresh install of Ubuntustudio 7.10 on my desktop computer. I'm now having issues with random freezing (total freezing; mouse still moves but cursor does not change, cannot click anything, no CPU activity), as well as some odd graphics issues.

First the freezing: it seems mostly to happen when I'm using firefox. I'll be using it for a minute or so and everything is fine, then everything just...stops basically. No little blinking light on the front of the computer tower, nothing. Mouse cursor stays whatever it was before. I have to turn it off and start over when that happens, and it happens every time.

The graphics issues seem to be somewhat varied. First of all, I noticed that sometimes when I start up, at the point when I should be seeing the splash screen loading, my monitor just does this crazy flashing on-off thing; it will show a black screen but be on, then it will say no signal, then black screen again, no signal, etc. After a few cycles of that, the login screen comes up. Then, sometimes, the gnome-settings-daemon (I think that's what it's called) will not start on startup. I can manually start it from a terminal, but it will not start itself. But then other times when I login it works fine.

Also, one time I was using firefox actually, and the screen just went black, as if the computer had gone to suspend, but it was still running. My monitor was on powersave though, so there was definitely no video output.

Also of note: I am not using the onboard video card, I am using an ATI Radeon 9250 instead, because the onboard card wouldn't support widescreen resolutions, and I have a 20" widescreen LCD monitor.

I did install the updates that came up when I started up, also.

Any help/suggestions? I can reinstall again if needed, and I might as well since I forgot to set up the /home drive to be on the separate drive that I have for it (I did the auto-partition thing instead...), but I have a feeling I would just get the same issues with a fresh install.

Thanks,
Dan

---

### Post by dbsoundman on 2008-04-03
Anyone? It seems now that most often my problem is a little bit different than the other freeze threads I've been reading. Instead of getting the situation I have had before where the screen freezes up but I can still move the mouse, I get an even more annoying situation where the video output seems to turn itself off randomly. For example, I was just using Firefox and surfing some webpages, when all of a sudden the screen goes black, and my monitor says "input not supported". Additionally, I have to hard restart because I cannot input any commands, not even alt-sysrq RSEIUB. Nothing happens. The webstream I was listening to did continue playing for a little bit after the black screen (~30 seconds), then it stopped as well. Anyone have tips on this one?


UPDATE: Just had another freeze, but this one only took like 2 minutes to happen. At first, it was just a standard screen freeze with a cursor I could still move but I couldn't input anything, so I let it sit, then the cursor froze as well. I'm wondering if I'm getting something that is locking up my CPU.

Thanks,
Dan

---

### Post by dbsoundman on 2008-04-03
OK, I have done some searching, and have no solution. Here's what I have tried:
-disabled powernowd, edited kernel with associated mods for that as well
-disabled acpid, apmd

I do not have compiz installed, so I can't do anything with that. The ATI drivers are all installed already, as part of the installation process, so I don't have anything I need to do with that, unless there is some other set of drivers. The ones I have are the generic ATI drivers found on synaptic. I found lots of solutions, but not many applied to me. I do not have a dual core setup, just an athlon XP, and I really haven't put anything on this computer yet other than the standard ubuntustudio programs.

It seems that I usually have problems when I am running things like firefox. Synaptic has not caused the problem so far, but I only ran synaptic once. Terminal does not do it. The login screen once froze up though. I did figure out that I can do the RSEIUB thing, I was just doing it wrong the first couple of times. No other keyboard commands work though when the freeze or blank screen happens.

The blank screen seems to occur more often than the freeze now, so it seems like my graphics drivers are just randomly shutting down or something. Also, I have no restricted drivers, since the ATI drivers I have came from synaptic.

I think this is about all I can figure out about my problems. I definitely need help, I'm sinking here. If I'm feeling gutsy (heh, heh) I may try a reinstall, or even just try out Hardy and see how that works out, but I would rather not get into development stuff, as I do get really sick of having to fix EVERYTHING all the time. Maybe I'll even try feisty again if all else fails. My main issue with feisty, or at least my install, is that things were starting to not work right; Ardour wouldn't install correctly, wine couldn't run Google Sketchup for some weird reason, Cinelerra didn't work (but works on my laptop with feisty), etc.

HEEELLLLLP!!!

-Dan

---

### Post by dbsoundman on 2008-04-03
NEW TRICK! ..

So I was using firefox to get to the quickstart recovery program page to do some experimentation, when all of a sudden, this happened:

[IMG]http://i200.photobucket.com/albums/aa62/dbsoundman/0403082053.jpg[/IMG]

It can only be explained by picture. The little square in the middle was my mouse cursor, which I could move. That pattern moved around, almost like TV static. Needless to say, I restarted. Does this mean anything special?

-Dan

---


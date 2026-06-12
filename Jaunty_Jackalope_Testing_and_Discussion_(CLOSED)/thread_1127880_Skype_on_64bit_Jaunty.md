---
title: "Skype on 64bit Jaunty"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by .Danny on 2009-04-16
Has anyone managed to get Skype working properly? I can get sound and ringing by setting everything to Pulse in Skype, but the Mic doesn't work.

It works fine through the OS though, when I test it with the Mic test in Sound options it works perfectly.

I have a Audigy 2 ZS sound card.

Any ideas how to fix this?

---

### Post by vlovich on 2009-04-17
I dunno, it worked for me (granted I broke it skype itself trying to upgrade to pulse 0.9.15 due to a really annoying CPU bug in 0.9.14 when there are two Linux machines running pulse 0.9.14).

Disable the checkbox that let's skype manage your audio settings & make sure your MIC isn't muted & is at full volume for recording (in the mixer).

Make sure that sound capture is set to PulseAudio sound server in gnome-control-center -> Sound.  Ensure that when you hit test, you can the mic input is routed to the speakers.  Make sure input in skype is set to pulse.

If you don't hear the mic routed to the speakers when you hit test, try setting it to the actual device (if you're not sure test them all until the mic is properly routed to the speakers).

If pulse still isn't working for skype recording, try setting your mic to your actual sound card (not pulse - the one that you found in gnome-control-center -> Sound).  If you're not sure which input to try, try all of them (might get quite annoying because skype's interface for testing the mic requires an actual call to be placed which is really slow when you want to quickly test a bunch of potential inputs).

You can also use the sound recorder that comes with Ubuntu to verify your settings (it picks up the value you use in gnome-control-center).

Hope this helps.

---

### Post by .Danny on 2009-04-17
Seems as if the upgrade to RC has fixed it. Got it working by trying randomly as you said.

This is a really annoying experience though, and something both Ubuntu and Skype should try to improve upon. I can't imagine someone less tech savvy browsing these forums for hours looking for a solution and trying out various options for 2 hours just to see it randomly starting to work.

---

### Post by mizel on 2009-04-17
Hi guys......
Help me.......i cannot login skype
Like Sign in failed Password inncorect
I have chek in web is fine I can log in into website
I just cannot login In software 

Please help 

Thanks...........&...........regards:(

---

### Post by vlovich on 2009-04-17
This actually is really skype's fault seeing as how they don't seem to be really pushing Skype development on Linux.  Their last release was about a year ago & it wouldn't be so bad except for their alsa implementation sucks so badly that it doesn't play very nicely with pulse.

There's not much Ubuntu can really do since Skype is propietary (hence the multitude of workarounds the community has come up with to try & getting it working).

That being said, I do believe that if you do a fresh install of Jaunty (not upgrade from a previous release), skype might work off the bat.

---

### Post by .Danny on 2009-04-17
> **vlovich said:**
> This actually is really skype's fault seeing as how they don't seem to be really pushing Skype development on Linux.  Their last release was about a year ago & it wouldn't be so bad except for their alsa implementation sucks so badly that it doesn't play very nicely with pulse.

There's not much Ubuntu can really do since Skype is propietary (hence the multitude of workarounds the community has come up with to try & getting it working).

That being said, I do believe that if you do a fresh install of Jaunty (not upgrade from a previous release), skype might work off the bat.

This was a fresh install. Skype didn't work. All the sound options had to be set to the exact sound card in Skype sound options (and you get like 10 choices for each card, so you can play the guess game on which it is).

I don't really blame Ubuntu for this issue, but perhaps they could try and push Skype a bit more on this.

---

### Post by vlovich on 2009-04-17
again it's skype's implementation that is causing problems.  there are simple workarounds to get it to work sound-out through pulse - sound-in might be a slightly different issue.

someone could put a package in the repository that sets up ubuntu for skype, but the problem with that is the pulse changes & the fixes change over time so its a hassle to maintain.

if you're not on a 64-bit machine, try upgrading to pulse 0.9.15*

*there's no guarantee it won't break skype on a 32-bit machine.  it just seems like the only ones complaining are us 64-bit users.

---


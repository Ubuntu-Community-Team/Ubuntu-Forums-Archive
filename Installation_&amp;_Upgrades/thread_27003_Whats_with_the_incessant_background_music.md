---
title: "Whats with the incessant background music?"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by ziphnor on 2005-04-14
Since i installed ubuntu yesterday, my computer has been playing a small piece of drum music(sounds african) in the background when the gdm login manager or KDE is running(Gnome doesnt work for some reason, which is what im trying to fix now). It sounds a bit like its looping. First i thought it was a stuck sound from the login and that my soundcard had a problem, but i can play mp3 files just fine, except they mix with the drum music :)

If i in the mixer mute all the outputs named EMU10K1 PCM the drumming disappears and i can play music normally. However, i find it disturbing to no that some process is wasting CPU cycles playing a silly piece of music, and i would like to stop it.

I have also noted that i have no less than 10 outputs with the EMU10K1 PCM label and 10 more with 'EMU10K1 PCM  Send' as well as 10 with 'EMU10K1 PCM  Send Routing'.

As far as i know i have 2 soundcards, an SBLive! value and an integrated AC97 crap soundcard which i belive i have disabled in the BIOS.

Any clues on solving this?

---

### Post by skoal on 2005-04-14
[QUOTE=ziphnor][...] As far as i know i have 2 soundcards, an SBLive! value and an integrated AC97 crap soundcard which i belive i have disabled in the BIOS.[/QUOTE]

I pretty much have the exact same setup.  I didn't hear that background music like you cited above.  I don't believe it's any issue with your soundcard, BIOS, or alsa mixer settings.

Is it reproduceable (and predictable) when you reboot?  What about just logging off then back in?  Same thing?  You might want to check the Gnome Application/Sound setup dialog.  I bet the boogeyman's in there somewhere.

---

### Post by ziphnor on 2005-04-14
[QUOTE=skoal]I pretty much have the exact same setup.  I didn't hear that background music like you cited above.  I don't believe it's any issue with your soundcard, BIOS, or alsa mixer settings.

Is it reproduceable (and predictable) when you reboot?  What about just logging off then back in?  Same thing?  You might want to check the Gnome Application/Sound setup dialog.  I bet the boogeyman's in there somewhere.[/QUOTE]

Thanks for responding. The problem is as reproducable as they get, it happens every single time, no matter if it reboot or relogin. You might be right about the gnome sound setup causing trouble, but i cant even login to Gnome(or even Gnome failsafe...) it justs hangs, i had to install kubuntu-desktop/KDE in order to be able to login :(

You wouldnt happen to know the file name of the Sound setup dialog so i can start it from KDE, would you?

---

### Post by ziphnor on 2005-04-14
I think the Gnome problem is related to the sound problem as you say. I changed my login manager to kdm, and now no strange music plays on the EMU10K1 PCM 'channel' in kmixer, so i guess gdm is trying to make some sound and it fails.

How can i run some sound setup on gnome to fix this without starting gnome?

---

### Post by skoal on 2005-04-14
[QUOTE=ziphnor]You wouldnt happen to know the file name of the Sound setup dialog so i can start it from KDE, would you?[/QUOTE]

Ooops!  Unfortunately no.

I guess if it occurs in KDE as well the gremlin inside your box might be scratching away at your soundblaster card/driver or some sound daemon.  I have the Sound Blaster Live! (not value).

Hmm...

Does it sound like a *hung* record that's skipping? Or just a replayable tune?  Know what I mean?  I guess if it's 'skipping' or 'hanging' then some process or device is left open as the offending process is caught in a racing situation.

I really don't know what could be causing this.  Sorry about that.  Have you read of anyone else in these forums having the same problem?  You might want to check that "sound is broken" sticky thread for a sol'n.

Best of luck.

---

### Post by speedman on 2005-04-14
You can launch the gnome sound preferences with this command:

gnome-sound-properties


Regards,

SM

---

### Post by eltadcirad on 2005-06-12
This looks like another case of 'inifinite drumming'. see also [http://www.ubuntuforums.org/showthread.php?t=25843](http://www.ubuntuforums.org/showthread.php?t=25843)

The sound you hear an eternal loop of /usr/share/sounds/question.wav

This is my current workaround.

To stop the incessant noise in gdm, edit a line /etc/gdm/gdm.conf to read

SoundOnLogin=false

For gnome to work, you need to prevent esd from starting, to do this login to any x session (failsafe terminal will do) and run gconf-editor. Browse to desktop->gnome->sound and uncheck enable_esd.

the basic problem is still here though, try playing a sound with aplay and you'll get the same king of looping. Oddly, apps which use the OSS compatibility layer (notably XMMS) seem to work fine.

I assumed this was a driver issue, but it's interesting that it seems to happen to various soundcards (I'm using snd_trident on a SIS7018).

---

### Post by eltadcirad on 2005-06-13
On my machine, this was related to ACPI and IRQ routing. the kernel paremeter 

pci=routeirq

solved the problem, and also enabled my wifi card (a netgear wg511) to work correctly.

---

### Post by Mustard on 2006-04-27
I didn't have much luck with the pci=routeirq solution.  I ended up using irqpoll on the kernel options and this got rid of the sound, but may have led to other issues (nvidia driver problems).  I haven't really worked it all out yet, but I'm doing a bit of experimenting. :)

I'm using a VIA motherboard, which I think could be a common factor with people who have this problem.  It would be good if people could confirm this.

---


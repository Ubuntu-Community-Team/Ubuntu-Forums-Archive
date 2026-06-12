---
title: "Bizarre Audio Behaviour After The Upgrade To Ubuntu 8.04"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by micheman26 on 2008-05-06
Hello I am writing from Italy. I have been using Ubuntu since the end of 2006. I learned Linux by myself on books because all my friends and colleagues are Windows only.
Today I have upgraded from Ubuntu 7.10 to 8.04. The upgrade went on smoothly.
Everything seemed OK until I played a videoclip using Totem. Video was perfect but audio kept silent.
Then I tried to play an audio CD: no audio.
Audio sounded perfectly only a few hours ago, when the old Ubuntu 7.10 was installed.
Strange yet true, audio works from the command line. I tried to play a MIDI file using timidity from the command line in the console and the sound was perfect as before the upgrade to 8.04.
When I try Totem, it plays video but remains silent.
I have tried to remove and reinstall Totem but to no avail.
Somehow the bug seems related to the graphic interface, because Gnome-based software like Totem and CD player remain silent while text-based software like timidity recognize and use the sound card.
The System -> Administration -> Hardware test recognizes the sound card and emits the trial sound.
I do not know what to do.
Thank you very much

---

### Post by mikey on 2008-05-06
same exact situation at my end. nvidia ck804 tests ok but refuses to play in 8.04

---

### Post by micheman26 on 2008-05-07
Well, after a new reboot this morning everything seems OK. Now Totem plays both video and audio.
Perhaps it is because in the System -> Preferences -> Audio menu I have switched from Automatic to ALSA (Advanced Linux Sound Architecture).
Try it with your sound card and tell me what happens, Mikey.
I hope this idea will solve your problem too.

---

### Post by mikey on 2008-05-08
we're having the same problem which after a bit of reading is common in hardy, as far as I understand regarding the 64 architecture. I have sound on login, not with the opening nor closing  of the desktop, on rhythmbox(with streaming audio) and totem but not on firefox 3. its seems to be a problem of flash 32 vs. 64  which so far I have not been able to address. I usually live inside linuxmint 4 which is basically gutsy but with a bit more flair. I've been having some wine issues there so I thought I'd try hardy but it looks like I'll have to wait on this one.I've tried konqueror, opera and weasel with no luck. there is a nswrapper approach which I have explored again without success. I'm also not happy with firefox 3 not supporting google toolbar. give linux mint a try if you're looking for ubuntu without the mess

---

### Post by nickko on 2008-05-08
It seems, that these problems are du to the fact, that a sound server (pulseaudio) is now used by default in hardy. The problem, is that pulseaudio is not compatible with everything (known issues with flash, skype and audacity for example), and sometimes doesn't want to play from several sources simultaneously.

If you don't use the advanced audio capabilities of pulseaudio, and just want "sound that works", try closing every application using sound, and then kill the pulseaudio process (killall pulseaudio in terminal, or using the system monitor).  Then try using your sound applications again...

It worked perfectly for me.

Sadly, the pulseaudio package is linked to the ubuntu-desktop package in hardy, so you cannot easily remove it.
But if killing pulseaudio works for you, you can make that happen on startup by adding a killall pulseaudio command in System>Preferences>Sessions.

This brought alsa back as the default sound manager, and everything works as in 7.10 for me.

---

### Post by kingof1981 on 2008-05-17
Hello Folks...

I must say that hardy is the worst version ever so far... audio problem with almost all applications... i can even hear music and do a videocall with skype at the same time... Kaffeine keeps crashing while watching dvb-s... the fstab and mtab file look's pretty mest up to me... after hardy i have over 12 drive's but i only have 5... Mozilla and ephany-browser keeps crashing while loading sites... or sometimes without a click... and many more things i've recognized but i don't wanna write a hole roman about it... but the most irritating problem is i don't can hear mixed audio...  what did happend, hardy is still growing up aguess... maybe it got fixed someday... go on folks... or does somebody else know how to fix this behaviour???

---

### Post by jimmybute on 2008-05-17
And yet another with the same problem :(

I also have no sound after upgrading from Gutsy to Hardy. I have sound at login but thats all. I'm running 32 bit version...

Why fix something that was not broke :confused:

---

### Post by pasyp on 2008-05-17
Hardy is a disaster for me, no sound and no wireless, all things that were perfect in Gutsy.
Is there a chance at patches soon or can i better go back to Gutsy.
Pasijp

---

### Post by jimmybute on 2008-05-18
I got my sound to work! 

On upgrading to hardy my alsa mixer volume settings were set to "0".

#-o  Why? 

Anyway...  open terminal - enter alsamixer  and turn them back up

---

### Post by Xavier Oddmon on 2008-05-19
As i've come to understand, most of these audio-related problems stem from the new pulseaudio system. I myself did not have any audio problems, but did not do an upgrade, instead I did a clean install (I really don't trust upgrade, I don't know why...) I have found that the audio tends to lag when running both compiz or pulseaudio, however. So I find that it helps to kill pulseaudio unless I really need it (ie bluetooth headphones)

---

### Post by iaculallad on 2008-05-19
Or you could read this HowTo (PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)) defined in the [link]("http://ubuntuforums.org/showthread.php?p=4928900")

---


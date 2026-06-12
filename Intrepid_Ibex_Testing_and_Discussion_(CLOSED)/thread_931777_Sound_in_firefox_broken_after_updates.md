---
title: "Sound in firefox broken after updates"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xaenyx on 2008-09-27
This is really weird.. So, all the sound worked fine before the uopdate, and (for the most part) after the update.  I checked the sound wizard thing and all of the audio output tests worked, and banshee/totem/etc work..  Problem is, flash videos don't have sound.  I checked and all of my volume controls are all the way up, libflashsupport is installed, and I tried doing dpkg-reconfigure libflashsupport as well. 

Any idea what's going on?

EDIT: Also, while I DO hear that drum sound when gdm starts, I do not hear the into sound when gnome starts..

---

### Post by psyke83 on 2008-09-27
> **xaenyx said:**
> This is really weird.. So, all the sound worked fine before the uopdate, and (for the most part) after the update.  I checked the sound wizard thing and all of the audio output tests worked, and banshee/totem/etc work..  Problem is, flash videos don't have sound.  I checked and all of my volume controls are all the way up, libflashsupport is installed, and I tried doing dpkg-reconfigure libflashsupport as well. 

Any idea what's going on?

EDIT: Also, while I DO hear that drum sound when gdm starts, I do not hear the into sound when gnome starts..

Are you on 64 bit or 32 bit? There have been changes to PulseAudio and Flash. The libflashsupport library is not and should not be installed anymore.

Check the [PulseAudio thread]("http://ubuntuforums.org/showthread.php?t=866965") for more information.

---

### Post by xaenyx on 2008-09-27
> **psyke83 said:**
> Are you on 64 bit or 32 bit? There have been changes to PulseAudio and Flash. The libflashsupport library is not and should not be installed anymore.

Check the [PulseAudio thread]("http://ubuntuforums.org/showthread.php?t=866965") for more information.

32 bit, following those instructions now.

---

### Post by xaenyx on 2008-09-27
Nope, followed the instructions but still no sound.

---

### Post by joakim2 on 2008-09-27
> **xaenyx said:**
> nope, followed the instructions but still no sound.

+1

Starting firefox from a terminal and trying something from youtube spits out a neverending stream of: ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

---

### Post by forumache on 2008-09-28
and again, I have to pulseaudio -k (thus killing pulse audio) in order to make it work. This happened too before/at the hardy release :(

---

### Post by plun on 2008-09-28
> **forumache said:**
> and again, I have to pulseaudio -k (thus killing pulse audio) in order to make it work. This happened too before/at the hardy release :(

Have you done everything in this howto  ?

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

Step 3 is really important for removing obsolete configs


You can also use Nautilus if you don't like rm commands.
**Ctrl-h** for hidden folders/files

---

### Post by forumache on 2008-09-28
Not everything, since I don't install PPAs. This would defeat the purpose of testing a clean Intrepid.

But I checked if libflashsupport was installed (it was not), I had nothing to remove from .pulseaudio/.asoundrc and I didn't set .libao since libao is not installed and I wouldn't install it if it is not pulled automatically by some dependencies.

---

### Post by plun on 2008-09-28
> **forumache said:**
> Not everything, since I don't install PPAs. This would defeat the purpose of testing a clean Intrepid.

But I checked if libflashsupport was installed (it was not), I had nothing to remove from .pulseaudio/.asoundrc and I didn't set .libao since libao is not installed and I wouldn't install it if it is not pulled automatically by some dependencies.

OK... psyke83 discusses this with Luke/TheMuso (Dev/Maintainer)

Also several bug reports about these issues for all versions we tested.

This folder can include obsolete settings >  **~/.pulse**

Without padevchooser and the Volume control its also difficult to
find out where you have your outputs. (if that fails)

libao and padevchooser and all PA tools must nevertheles be clarified for final Intrepid.

---

### Post by kostkon on 2008-09-28
> **xaenyx said:**
> This is really weird.. So, all the sound worked fine before the uopdate, and (for the most part) after the update.  I checked the sound wizard thing and all of the audio output tests worked, and banshee/totem/etc work..  Problem is, flash videos don't have sound.  I checked and all of my volume controls are all the way up, libflashsupport is installed, and I tried doing dpkg-reconfigure libflashsupport as well. 

Any idea what's going on?

EDIT: Also, while I DO hear that drum sound when gdm starts, I do not hear the into sound when gnome starts..
One is for sure, that you don't need the *libflashsupport* package, since as I can see you should be using *Flash 10*, am I right? Intrepid comes with *Flash 10*?

*libflashsupport* is only useful with Flash 9, it allows it to work with *PulseAudio*.

---

### Post by rosswmcgee on 2008-09-30
I have Flash 10 but no sound in Firefox videos. What is the fix?

---

### Post by philinux on 2008-09-30
I've just done a complete re-install of the daily build and just done all the updates. 32 bit

I installed ubuntu-restricted-extras as usual.

Went to sky news web site and flash is working fine with sound. I did think at first that it wasn't working. I had to turn the volume up on pcm and front.

---

### Post by rosswmcgee on 2008-09-30
How do follow your example?

---

### Post by BwackNinja on 2008-09-30
do you have pavucontrol and does the stream appear there?

---

### Post by rosswmcgee on 2008-09-30
I do not know if I have pavucontrol, that is a new one on me?

---

### Post by rosswmcgee on 2008-09-30
Found it in snynoptic. Should I install it?

---

### Post by BwackNinja on 2008-09-30
yeps, it will probably also install things like padevchooser and such (pulseaudio has some nice tools :D)

---

### Post by rosswmcgee on 2008-09-30
Ok so what will it do for the sound problem?

---

### Post by BwackNinja on 2008-09-30
If it doesn't show up in pavucontrol when playing flash, then that means it _isn't_ using pulseaudio at all, so the solution would be fairly simple. If it does show up in pulseaudio, making sure it is going to the right device might help.

---

### Post by rosswmcgee on 2008-09-30
Ok turned on pulse audio, ran utube, no sound still.

---

### Post by psyke83 on 2008-09-30
> **rosswmcgee said:**
> Ok turned on pulse audio, ran utube, no sound still.

I suggest you read Appendix B of [this]("http://ubuntuforums.org/showthread.php?t=789578") guide in order to understand how PulseAudio works (and thus provide more useful information).

If you're using 64 bit Ubuntu though, Flash isn't working correctly at the moment, but the fix will come soon.

---

### Post by rosswmcgee on 2008-09-30
no thirty two bit, but thanks, just wonder what the diff is between ibex and heren on this issue.

---

### Post by ktp on 2008-09-30
> **rosswmcgee said:**
> no thirty two bit, but thanks, just wonder what the diff is between ibex and heren on this issue.

Could you please try to do the following:

1. Kill pulseaudio, either by using "killall pulseaudio" or "pulseaudio -k"
2. Remove all .pulse files from your home directory, "rm -r ~/.pulse*"
3. Move any .asoundrc files away to a temporary directory, of if you have nothing in them that you want to keep, delete them.
4. Restart pulseaudio, either by rebooting, logging out and back in, or running "pulseaudio -D --log-target=syslog"

---

### Post by rosswmcgee on 2008-10-01
I will give it a try.

---

### Post by rosswmcgee on 2008-10-01
killallpuseaudio
bash: killallpuseaudio: command not found
rosswmcgee@rosswmcgee-desktop:~$ pulseaudio -i
pulseaudio: invalid option -- 'i'
E: main.c: Failed to parse command line.
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by rosswmcgee on 2008-10-01
no .asoundrc files found, did kill pulseaudio will now reboot.

---

### Post by rosswmcgee on 2008-10-01
OK did all that/ still audio in videos.

---

### Post by ktp on 2008-10-01
> **rosswmcgee said:**
> killallpuseaudio
bash: killallpuseaudio: command not found
rosswmcgee@rosswmcgee-desktop:~$ pulseaudio -i
pulseaudio: invalid option -- 'i'
E: main.c: Failed to parse command line.
rosswmcgee@rosswmcgee-desktop:~$

it should be "killall puseaudio" you forgot the space.

Sorry about the wrong option...it should be -k not -i

---

### Post by rosswmcgee on 2008-10-01
Voila! got the sound and thank you!

---

### Post by rosswmcgee on 2008-10-03
After todays updates, no audio again with videos or slacker radio for instance. Tried previous terminal fixes, to no avail. Suggestions Please and thank you!

---


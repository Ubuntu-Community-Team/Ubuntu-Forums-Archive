---
title: "No system sounds after Feisty upgrade"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by punkybouy on 2007-08-11
I just upgraded from Edgy to Feisty.  System sounds no longer play.  My TV time TV tuner works just fine with sound and internet radio stations play just fine too.  I get the bongo sound when the login splash screen shows up but when I log in there is no login sound.  If I go to System\Preferences\Sound I can test the sound card in the "Devices" tab and it works just fine but if I go to the next tab for "sounds" the arrow next to login and logout are not green and don't play.  If I select some other wav file it does not play either.  Anyone have any suggestions?

---

### Post by punkybouy on 2007-08-11
In addition I ran the live CD and system sounds work fine under that.  Is there any way to reinstall the sound package?

---

### Post by punkybouy on 2007-08-13
More info.  When I run this command as root it plays.
 aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
When I run it as my user ID I get:
 aplay /usr/share/sounds/login.wav
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:VT82xx
aplay: main:550: audio open error: No such file or directory

My user ID is in the audio group.
Anybody have any ideas?

---

### Post by punkybouy on 2007-08-13
Sorry, the colons come out as sad faces

---

### Post by punkybouy on 2007-08-14
Fixed it. After a lot of Googling using the errors as search terms,  I created a new user which could play all system sounds.  I noticed the new user did not have an asoundrc and asoundrc.asoundconf files (these are hidden files) so I renamed them in my user configuration and the problem was solved.  You could just delete them too.

---

### Post by smokey_58au on 2007-08-20
Thanks punkybouy.  I have just upgraded to Feisty and had the same issue.  Renamed these 2 files in my home directory and it fixed the problem.:)

---


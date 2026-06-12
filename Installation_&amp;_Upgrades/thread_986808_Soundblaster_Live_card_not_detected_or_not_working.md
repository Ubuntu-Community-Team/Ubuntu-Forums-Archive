---
title: "Soundblaster Live card not detected or not working"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by tee2 on 2008-11-18
I just put a SoundBlaster Live! soundcard in my brothers ancient computer because the onboard sound wasn't working and I was hoping this would. Still no sound so I reinstalled alsa and some other sound related packages hoping that it would get things going but still no sound. Any help would really be appreciated. This is Xubuntu 8.10 btw.

---

### Post by tee2 on 2008-11-19
Anyone have any ideas??

---

### Post by tee2 on 2008-11-20
bump 

:confused:

---

### Post by tee2 on 2008-11-21
bump

---

### Post by Shazaam on 2008-11-22
First, make sure that ANY onboard sound chips are disabled in the pc's bios. Then go to Applications>Accessories>Terminal and open it. Enter this...
```
alsamixer
```
Along the bottom you will see boxes thar are either 00 or MM. Using your arrow keyboard keys move to the ones that are MM and hit the m key. This will unmute the settings (changes them to OO). Play around with them to see if it works, the up and down arrow keys change the levels.
If after this and still no sound, go to System>Preferences>Sound. On the Devices tab change ALL but the bottom one to ALSA, Default Mixer Tracks change to SBLive.
If it now works then you might want to disable pulseaudio (or reconfigure it).

---

### Post by tee2 on 2008-11-22
> **Shazaam said:**
> First, make sure that ANY onboard sound chips are disabled in the pc's bios. Then go to Applications>Accessories>Terminal and open it. Enter this...
```
alsamixer
```
Along the bottom you will see boxes thar are either 00 or MM. Using your arrow keyboard keys move to the ones that are MM and hit the m key. This will unmute the settings (changes them to OO). Play around with them to see if it works, the up and down arrow keys change the levels.
If after this and still no sound, go to System>Preferences>Sound. On the Devices tab change ALL but the bottom one to ALSA, Default Mixer Tracks change to SBLive.
If it now works then you might want to disable pulseaudio (or reconfigure it).

When I try and run alsamixer I get this

```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Thanks for the reply by the way. :)

---

### Post by tee2 on 2008-11-24
bump

---

### Post by tee2 on 2008-11-27
bump

---

### Post by faustism on 2008-11-29
I am having a similar problem. I get that error at alsamixer and i dont know what to do.  I am thinking that there is a problem in xubuntu itself.  Does anyone NOT get an error message when they run "alsamixer" ?

[Heres my thread]("http://ubuntuforums.org/showthread.php?t=975553")

---

### Post by tee2 on 2008-11-29
> **faustism said:**
> I am having a similar problem. I get that error at alsamixer and i dont know what to do.  I am thinking that there is a problem in xubuntu itself.  Does anyone NOT get an error message when they run "alsamixer" ?

[Heres my thread]("http://ubuntuforums.org/showthread.php?t=975553")

Are you using a soundblaster live! card?

---

### Post by faustism on 2008-11-29
no I'm not, but I dont think that is the problem. (well maybe it is but I think theres another) I think that something isn't installed right. I am using a Audio Drive ES1869 card.

---

### Post by faustism on 2008-12-21
i got my sound to work. im not sure if your having the same problem though. maybe u want to try what i did... [http://ubuntuforums.org/showthread.php?p=6411275#post6411275]("http://ubuntuforums.org/showthread.php?p=6411275#post6411275")

---


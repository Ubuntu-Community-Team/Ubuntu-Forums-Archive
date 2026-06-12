---
title: "Ubuntu Karmic Koala Bad Sound Quality!:( same problem??"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by saggitheman on 2009-10-19
Hi.

I updated from Jaunty to Karmic Beta, but the sound quality SUCKS!
Anyone with the same problem?

It sounds like my speakers are blown:( I got a NAD C372 amp with Eltax Millennium 500 speakers, so I want to get full use off it:D 
Is there anyway to get the old sound settings back? The one from Jaunty with the PCM and the Headphone settings... Now it's just the main volum settings:(  

On the older version (Jaunty's settings) I needed to set the PCM right over the middle or else it was the same sound as now... so it could be helpful to get the old settings back:)

Thanks in advanced:)

---

### Post by dabl on 2009-10-19
> **saggitheman said:**
> Hi.

Is there anyway to get the old sound settings back? 



Assuming you are using ALSA and have the right driver installed, 

```
sudo apt-get install alsamixergui
```

is my favorite.  If you don't see a PCM channel, you'll need to add it -- and make sure it is unmuted. Possibly other channels that your sound chip has available are not being used, too.

---

### Post by ajgreeny on 2009-10-19
Not tried karmic yet but in previous versions you can right click on the volume icon in the panel, choose Preferences and change the device and track that the volume control acts on.  Perhaps that has gone now, and you are just left with one of the pulse options, not nearly as useful, nor with as many tracks showing.

---

### Post by rtalcott on 2009-10-19
Karmic sound is fine here...I take the spdif out to a DAC and into the stereo....
rt

---

### Post by saggitheman on 2009-10-19
Not working. How do I add the PCM??

---

### Post by saggitheman on 2009-10-19
Okay, I'm going to explain to you;)

I have upgraded from Jaunty to Karmic Beta. Karmic has a new audio settings thing... It doesn't show any more than the main volume, not PCM or Headphones. It's not possible to add some sort off other options like PCM to the settings, so that's why I wonder if it's posible to install the old ALSA settings manager???
(You know what i'm saying?)

Thanks for all replays:)

---

### Post by perfectska04 on 2009-10-19
I'm experiencing similar issues.

After an install from a daily live this weekend, there was no sound whatsoever. The next day, there were some pulseaudio upgrades that enabled it but now there are cracks and pops before and after any song/video/flash is played.

I can live with that until it gets fixed. However, the most annoying part is that the new system does not allow for speakers to be muted after plugging in my headphones, like Jaunty's did. There is an option to select between "Analog Output" and "Analog Headphones", but when choosing "Analog Headphones" there is no sound working for anything. The only way to get sound to work is by choosing "Analog Output", but then muting speakers when headphones are plugged in ceases to work as stated above - and it can be quite frustrating.

For the record, this is on an ALC883 codec. I believe I've seen a related bug in launchpad, but there seems to be no fix for it as of now.

---

### Post by ell02 on 2009-10-19
Type alsamixer in the terminal. I found some settings were not cranked. Also this is a good link i used for game related skipping.



[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

---

### Post by LittleKoy on 2009-10-20
Same problem here. Just did a fresh install, and sound quality is ugly to be nice. A lot of crackling. Reducing the volume to about 30% and turning up the speakers vastly I have a decent sound quality, but you can still hear some crackling in the background.

---

### Post by saggitheman on 2009-10-20
Thanks for answers:D
I have found out a wired thing... If I set the to 3/4, the shitty sound goes away:D:D But I have a very good amplifier (NAD C372), so I don't turn the volume on it up to max on it...(no one does acctually) so I can just set the Ubuntu volume a little bit lower, and turn up the amp:D:D

I will wait for the final/release candidate to come out and see if it's bin any better. If not, I think I will just screw it;)

Thanks for all great answers:D

---

### Post by jamlam on 2009-10-20
> **saggitheman said:**
> Thanks for answers:D
I have found out a wired thing... If I set the to 3/4, the shitty sound goes away:

You'll find this isn't an Ubuntu specific problem... If you're using an external amp through an analog output (i.e. not SPDIF via coax or optical) you'll get the best sound by setting the volume to just below maximum on the PC. 

Anything over this and you'll start overloading the output on your soundcard = distorted nasty sounds. You also don't want to set it too low otherwise you'll start hearing background hiss, so 3/4 volume should be about perfect!

---

### Post by saggitheman on 2009-10-20
I had no problem with ugly sound on the other Ubuntu versions... But there I had the PCM and Headphone settings. So my settings on older versions was:
Main Volume: Full
Headphones: Full
PCM: About 3/4 (got nasty sound if full)

So it could have been the PCM??:D

---


---
title: "Lubuntu 13.10 - Volume control is not working, not visible on panel, etc."
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by NuxNik on 2013-12-29
Lubuntu 13.10
This install is an upgrade from 13.04 (and frankly, it's been an anal pain...)

Volume control has suddenly disappeared from my panel
There were no changes/upgrades/installs/etc. to the system from the time it was working and now.

The little speaker icon has disappeared on the panel

Going into the panel setting/panel applets, right-clicking on volume control makes a terminal appear and immediately disappear.
  Same thing if you click on "edit" with volume control highlighted

In effect whatever the definition behind "volume control" was. is now borked

As a result I have no sound and no way to have sound.

All the documentation that I have seen seem to segue into installing something else.

I just want to know how to get what comes with lubuntu, running again

---

### Post by sudodus on 2013-12-29
I often use Lubuntu, and I like to add PulseAudio and PavuControl. That will improve the control of the audio system. The only exception might be if the computer is very old and cannot manage the extra work-load of those packages.

```
sudo apt-get install pulseaudio
sudo apt-get install pavucontrol
```

---

### Post by Rex Bouwense on 2013-12-29
This a place to start when you have no sound in Lubuntu.
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17)

---

### Post by mörgæs on 2014-01-01
> **NuxNik said:**
> 
This install is an upgrade from 13.04 (and frankly, it's been an anal pain...)

Often they are. In stead of struggling with this present system have you considered a clean intstall of 13.10?

---

### Post by NuxNik on 2014-01-01
> **mörgæs said:**
> Often they are. In stead of struggling with this present system have you considered a clean intstall of 13.10?

Considering that everything worked fine in 13.04. 
I really NOT happy with the notion of doing a so-called clean install of 13.10
Don't want to have to re-install all my other stuff

Also, if the upgrade from 13.04 to 13.10 is borked, why should I even imagine that a straight install of 13.10 would be any different.

Lubuntu is already flawed in that gparted is part of the live version but does not get installed with either 13.04 or 13.10
One would presume that a system tool usefull to manage an install would also be available to manage the system
But that's just me and 40 years of IT and systems engineering.

This is the kind of sloppy niggly nonsense that has kept the promis of Linux unrealised and left people continuing instead with  Windows all these years.

---

### Post by NuxNik on 2014-01-01
> **sudodus said:**
> I often use Lubuntu, and I like to add PulseAudio and PavuControl. That will improve the control of the audio system. The only exception might be if the computer is very old and cannot manage the extra work-load of those packages.

```
sudo apt-get install pulseaudio
sudo apt-get install pavucontrol
```


Isn't the notion of Lubuntu to keep this light simple and streamlined ?

I would like to get what comes with Lubuntu working instead of adding stuff and porking it.

---

### Post by NuxNik on 2014-01-01
> **Rex Bouwense said:**
> This a place to start when you have no sound in Lubuntu.
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17)


That may be valid for Ubuntu but apparently pulseaudio is NOT installed with Lubuntu, so this solution is already a fail at step 1.

I really would like to solve this problem with what Lubuntu came with instead of porking it up with more stuff.

---

### Post by mörgæs on 2014-01-02
> **NuxNik said:**
> 
Also, if the upgrade from 13.04 to 13.10 is borked, why should I even imagine that a straight install of 13.10 would be any different.


I do imagine that, and with 40 years of experience I find it strange that you have not experienced a similar situation before.

---

### Post by NuxNik on 2014-01-05
> **mörgæs said:**
> I do imagine that, and with 40 years of experience I find it strange that you have not experienced a similar situation before.


Indeed, my experience is that if one form of something is borked, the odds of another form of it being the same are pretty good.
Which explains my reluctance of doing a clean install as a solution

---


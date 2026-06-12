---
title: "No sound in Karmic Koala"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tarkers on 2009-08-17
Hey, just upgraded from Jaunty to Karmic and as soon as my machine rebooted from the upgrade I'm completely without sound, and can't even add the volume control, it says (Deprecated) beside it.

I've done a couple searchs, and found people with the same problem, but no results anyone know what the cause of this is?

---

### Post by running_rabbit07 on 2009-08-17
> **Tarkers said:**
> Hey, just upgraded from Jaunty to Karmic and as soon as my machine rebooted from the upgrade I'm completely without sound, and can't even add the volume control, it says (Deprecated) beside it.

I've done a couple searchs, and found people with the same problem, but no results anyone know what the cause of this is?

Have you filed a bug report through launchpad?

Once the fix is found, it will happen in a future release.

Stay tuned as someone may post a way to fix it yourself.

---

### Post by Tarkers on 2009-08-18
I couldn't quite figure out how to file the bug with launchpad, I seem to have got in a login loop through UbuntuOne

Anyways, I hope someone can help me out, I've been working on this most of the day and can't find any resolution.

---

### Post by Elfy on 2009-08-18
moved to karmic forum

---

### Post by chronosMark on 2009-08-18
I've been experiencing a lot of issues with sound under Karmic as well. 

[LIST]
[*]Initial install of Alpha 2 sound worked
[*]Install of Alpha 3 sound broke later I discovered it was working but only through headphones nothing I tried would make it work through the laptop speakers
[*]Nearing the end of Alpha 3 there was a kernel update and then a pulse audio update this fixed the issue.
[*]Updating to Alpha 4 totally broke the sound for the system.
[/LIST]
I haven't managed to fix the issue myself but I think its something to do with a driver or kernel module not being loaded. Unfortunally after the problem was solved I deleted all the logs and notes I had releating to the issue. 

In your case you might want to try following the step by step on here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) to see if it can solve your issue or at least diagnose exactly what the problem is.

---

### Post by Tarkers on 2009-08-18
> **chronosMark said:**
> I've been experiencing a lot of issues with sound under Karmic as well. 

[LIST]
[*]Initial install of Alpha 2 sound worked
[*]Install of Alpha 3 sound broke later I discovered it was working but only through headphones nothing I tried would make it work through the laptop speakers
[*]Nearing the end of Alpha 3 there was a kernel update and then a pulse audio update this fixed the issue.
[*]Updating to Alpha 4 totally broke the sound for the system.
[/LIST]
I haven't managed to fix the issue myself but I think its something to do with a driver or kernel module not being loaded. Unfortunally after the problem was solved I deleted all the logs and notes I had releating to the issue. 

In your case you might want to try following the step by step on here [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) to see if it can solve your issue or at least diagnose exactly what the problem is.

Hey ChronosMark, I'm following those instructions, I'm not sure if you're very familiar with the steps yourself but I figured I should ask here anyways and someone might know.  following those steps it directs me to the ALSA project to see if they have my chipset there (Which they should, sound was fine in Jaunty) anyways, I can't seem to find the mentioned dropdown to search for any chipsets, did their website change somewhere along the way?  If anyone knows where I can search for my chipset that would be awesome.

Edit: here's my driver information, I figured I might as well throw it in here too.

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 8213
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

I notice it's using Intel ICH for a driver, which used to be listed as a sound device in Jaunty, but I didn't use it since it also had another one that did work.

---

### Post by chronosMark on 2009-08-18
I couldnt find a page exactly as described by that article but I think this page does the job [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Last thing I found is that when I do 'alsactl init' it gives some error about not being able to get the correct module or something (will put the exact one when I get home and can run the command).

---

### Post by sintacto on 2009-08-18
I hope this helps someone
 
I have to unmute headphones in alsamixer
after every reboot (not often)

then sound works 
2.6.31-5-generic
9.10 alpha 4

---

### Post by Tarkers on 2009-08-18
Apparently my headphones do work, (durr) I probably should have checked that, according to cat /proc/asound/modules I have:

 0 snd_intel8x0
 1 snd_usb_audio

The first being my onboard soundcard, the second being my usb headphones soundcard.

So obviously they both are in there correctly, but I can't figure out where to change it to use my onboard sound by default, I think 9.04's volume controls had the option in the GUI to switch between them, but I can't even get to that volume control anymore, it doesn't seem to exist in 9.10

---

### Post by curley_sue on 2009-08-19
> **Tarkers said:**
> Hey, just upgraded from Jaunty to Karmic and as soon as my machine rebooted from the upgrade I'm completely without sound, and can't even add the volume control, it says (Deprecated) beside it.

I've done a couple searchs, and found people with the same problem, but no results anyone know what the cause of this is?


had a similar problem on a fresh installed Karmic (thinkpad t61).
deleted ~/.pulse
( rm -r ~/.pulse )
and restarted pulseaudio
( killall pulseaudio )

solved for me (make sure speakers and headphones are not muted:
alsamixer

(the square underneath the headphones & speakers should be green by clicking "m")
hope that helps

---

### Post by chronosMark on 2009-08-19
> **curley_sue said:**
> 
deleted ~/.pulse
( rm -r ~/.pulse )
and restarted pulseaudio
( killall pulseaudio )


This fixed my sound thanks curely_sue.

---

### Post by MKdx on 2009-08-19
Yes, for some reason the sound got muted after the update I did (included rc6 kernel). You can right-click the volume control applet -> sound preferences, and check if the audio is muted in the master volume or applications one. This did it for me.

---

### Post by Cresho on 2009-08-19
this is going to be a problem for audigy users since you still need alsa-utils from jaunty and not from karmic to force enable audigy as the primary audio recorder.  I had issues with mic not wanting to record so I had to kill and uinstall pulseaudio. and install ... 

ill post some notes.  It's mixed up a bit but its what I currently use to fix all the encarnations of ubuntu for my sound card and the only way i managed to get audio working.  In karmic koala, something new happened.  I cannot change the boot sound or use the theme sound since it all now runs through pulseaudio sound manager which i think really sucks at the moment.

```
********************************************************************************
********************************************************************************
********************************************************************************
jaunty removing pulseaudio******************************************************
********************************************************************************
#killall pulseaudio
#sudo apt-get remove pulseaudio
#sudo apt-get install esound
#sudo apt-get install gnome-alsamixer
#sudo apt-get install
#install jaunty alsa-utils_1.0.18-1ubuntu11_amd64.deb
#sudo rm /etc/X11/Xsession.d/70pulseaudio (do not do this just incase)
#Reboot system

use gnome-alsamixer to keep a check on only tone, mic boost, audigy analog/digital output jack
for alsamixer mic to work, i bumped up the mic record and analog mix rec up to work, I #alsamixer or created a button to execute #gnome-terminal --execute alsamixer
********************************************************************************
********************************************************************************
********************************************************************************
test audio in also terminal*****************************************************
********************************************************************************
#speaker-test -Dplug:surround51 -c6 -twav
#speaker-test -Dplug:surround51 -c6 -l1 -twav
#speaker-test -Dplug:surround40 -c4 -l1 -twav
#speaker-test -Dplug:surround51 -c6 -l1 -twav
#speaker-test -Dplug:surround71 -c8 -l1 -twav
********************************************************************************
********************************************************************************
********************************************************************************
pulseaudio 5.1******************************************************************
********************************************************************************
#sudo gedit /etc/pulse/daemon.conf

Uncomment the line containing:
default-sample-channels = 2

and replace '2' with '6' (if you have a 7.1 card, replace '2' with '8')
Restart the window manager and enjoy the new sound!
********************************************************************************
********************************************************************************
********************************************************************************
mic fix*************************************************************************
********************************************************************************
#sudo apt-get install asoundconf-gtk
So then I created a script

##!/bin/bash
#sleep 10 && asoundconf set-default-card Audigy2;

and forced executable and forced it to autoboot in sessions under preferences.  Now my sound recorder works

other commands
#asoundconf set-default-card Audigy2
#asoundconf list
#


on another note, i did an install of openAl in synaptics.  All this was necessery to get sound in quake wars working and also mic.  without this, it is totally impossible
```

---

### Post by zoomy942 on 2009-08-20
> **curley_sue said:**
> had a similar problem on a fresh installed Karmic (thinkpad t61).
deleted ~/.pulse
( rm -r ~/.pulse )
and restarted pulseaudio
( killall pulseaudio )

solved for me (make sure speakers and headphones are not muted:
alsamixer

(the square underneath the headphones & speakers should be green by clicking "m")
hope that helps

worked for me too.  something i am wondering is if my tablet is auto shutting off the intel HDA.  i ask becasue on earlier version of ubuntu, if i enabled the power management of the audio, the mute button would flicker before a sound played.  its doing that again.

---

### Post by Claus7 on 2009-09-06
Hello,

at the first boot after upgrade I had sound. Yet, on the second reboot onwards I had no sound as well.
This:
> **chronosMark said:**
> This fixed my sound thanks curely_sue.
solved the issue for me as well!

Regards!

---

### Post by beow on 2009-10-03
Fixed my sound by only un-muting using the 

$ alsamixer

Sound came back when I un-muted (toggling with key "m") the very intuitively named control "LFE"...

---

### Post by TheFuzz4 on 2009-10-04
> **sintacto said:**
> I hope this helps someone
 
I have to unmute headphones in alsamixer
after every reboot (not often)

then sound works 
2.6.31-5-generic
9.10 alpha 4

Thanks that did the trick for me.

---

### Post by Corindatara on 2009-10-06
> **curley_sue said:**
> had a similar problem on a fresh installed Karmic (thinkpad t61).
deleted ~/.pulse
( rm -r ~/.pulse )
and restarted pulseaudio
( killall pulseaudio )

solved for me (make sure speakers and headphones are not muted:
alsamixer

(the square underneath the headphones & speakers should be green by clicking "m")
hope that helps

I had a HUGE problem getting pulse working in Jaunty, but your method fixed my issues in Karmic easily. Guess the settings just needed to be reset.

---

### Post by BAiHAX on 2009-10-06
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

This method is really work. Original message here: [http://ubuntuforums.org/showthread.php?t=1280009](http://ubuntuforums.org/showthread.php?t=1280009)

---

### Post by jdelgado on 2009-10-23
> **BAiHAX said:**
> # first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

This method is really work. Original message here: [http://ubuntuforums.org/showthread.php?t=1280009](http://ubuntuforums.org/showthread.php?t=1280009)

This worked for me, after trying also the previous suggestions.

thanks a lot

---


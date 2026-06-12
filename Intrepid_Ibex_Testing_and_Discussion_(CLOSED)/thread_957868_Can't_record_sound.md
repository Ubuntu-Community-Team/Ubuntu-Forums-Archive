---
title: "Can't record sound"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dcarpenter on 2008-10-24
I have had a problem since the alpha releases of Intrepid when I try to record sound via the microphone.  I have an Audigy 2 sound card.  Recording works in Hardy after a few tweaks (enabling Analog Mix input, etc).  My problem in Intrepid is that the settings that I choose in the Volume Control applet do not 'stick'.  I toggle recording to 'on' for Master Input, Microphone, and Analog Mix, however, when I close Volume Control and reopen it, my settings are reverted back to their 'off' state.  I have also noticed that when using the Sound Recorder, when I start recording the Length that is displayed increases at ~1 minute per second.  I record for 4-5 seconds and the length displays as 5-6 minutes.  This is a major bug for me as I rely on skype heavily.  I would stay with Hardy but I need the newer Kernel as it solves a few other issues I was having.  Any ideas as to why my recording is so borked?

---

### Post by dcarpenter on 2008-10-24
uploaded a youtube video using recordmydesktop so you can see exactly what I am talking about.  [http://www.youtube.com/watch?v=XQa0KdgF_xo](http://www.youtube.com/watch?v=XQa0KdgF_xo)

---

### Post by dcarpenter on 2008-10-24
anyone?:confused:

---

### Post by fabertawe on 2008-10-25
> **dcarpenter said:**
> I have had a problem since the alpha releases of Intrepid when I try to record sound via the microphone.  I have an Audigy 2 sound card.  Recording works in Hardy after a few tweaks (enabling Analog Mix input, etc).  My problem in Intrepid is that the settings that I choose in the Volume Control applet do not 'stick'. [snip]

I have an Audigy 2 also. You could try the following...

'System -> Administration -> Services' and make sure 'Audio settings management (alsa-utils)' is ticked.

If that doesn't do it then bring up the mixer in a terminal
```
alsamixer -c 0
```
Use the arrow keys (left/right) to navigate and (up/down) to alter the levels and use TAB to switch between 'Playback', 'Capture' and 'All'. Once you've set the levels it's 'ESC' to exit. Then save with
```
sudo alsactl store 0
```

Hopefully this will sort things out.

---

### Post by mirhciulica on 2008-10-25
Same problems here! 
A couple a days ago I made the mic work, I don't know how. Skype worked even if the mic was off :confused: 
Now it don't works anymore! I tried fabertawe's tips, but still it doesn't work :(
I need skype!
I hope somebody will get the mic working

---

### Post by dcarpenter on 2008-10-25
I tried both things that fabertawe suggested, and neither helped me with anything.  I would really like to be able to upgrade to 8.10 but if I can't get this audio problem sorted out I guess I will be stuck with 8.04 for a while longer.

---

### Post by dcarpenter on 2008-10-25
Trying this: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

I'll post an update when I'm done.

---

### Post by dcarpenter on 2008-10-25
Ok, so I tried the process in the pulse audio (distilled) thread and I totally killed my sound some how.  I am posting this from the 8.10 rc livecd.  I think I have found a solution to the problem however.  Just go to System > Preferences > Sound and under 'Sound Capture' choose Audigy 2 [SB0240] (rev.4, serial: 0x10071102) ADC Capture/Standard PCM Playback (ALSA).  Sound recording should work now assuming you have the correct settings in the mixer applet.  The recording inputs are still toggled to the off setting every time I close the volume control window but the settings are saved correctly, just a bug in what is displayed I guess.  I really don't know what was wrong with the default settings but I can record sound now, thats all that matters.

---

### Post by fabertawe on 2008-10-27
> **dcarpenter said:**
> I think I have found a solution to the problem however.  Just go to System > Preferences > Sound and under 'Sound Capture' choose Audigy 2 [SB0240] (rev.4, serial: 0x10071102) ADC Capture/Standard PCM Playback (ALSA).  Sound recording should work now assuming you have the correct settings in the mixer applet.  The recording inputs are still toggled to the off setting every time I close the volume control window but the settings are saved correctly, just a bug in what is displayed I guess.  I really don't know what was wrong with the default settings but I can record sound now, thats all that matters.

How strange... I hadn't actually tried recording for a while but now I have I find I have the same problem as you! Like you say, setting 'ADC Capture/Standard PCM Playback (ALSA)' as default capture in sound preferences allows recording in general to work but with recording input ('Line-in' in my case) always displayed as disabled when re-opening Alsa mixer.

I've also found that recording through Skype will not work no matter what unless I change 'Device' to 'SB Audigy (OSS Mixer)' in Alsa mixer. Skype worked perfectly previously with Alsa.

---


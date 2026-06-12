---
title: "Microphone not working with skype ubuntu 9.10"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by huzefa.mansoorali on 2009-10-24
hi,

I am testing Ubuntu 9.10 on my Acer Aspire 5720z notebook. On previous versions of Ubuntu 8.04+ the default sound server was ALSA and reading certain threads i was able to configure mic for skype using ALSA settings but in karmic koala sound settings are different.

Karmic Koala doesnot seem to rely on ALSA, although ALSA depositories are pre-installed and can be configured as default sound server.

although certain threads refer to ALSA patch in ubuntu 9.10 like the following one but that solution doesnt seem to work even

*In order to get the microphone to work when using Ubuntu 9.10 Beta on an EeePC 900a you only need to patch the ALSA configuration file:
Patching of the ALSA configuration file (/etc/modprobe.d/alsa-base.conf)
2. Enter 'sudo gedit /etc/modprobe.d/alsa-base.conf'
3. Search in the file whether a line including 'snd-hda-intel' exists, if so please delete that line
4. Add the following two lines to the configuration file:
5. Save the ALSA configuration file and close the editor (gedit)
Have fun with Ubuntu 9.10, it is a great look & feel OS for the EeePC 900a
vBulletin 2000 - 2009, Jelsoft Enterprises Ltd. Ubuntu Logo, Ubuntu and Canonical Canonical Ltd. Tango Icons Tango Desktop Project. bilberry*

Any help?

Huzefa

---

### Post by mperry on 2009-10-24
Here is what I found with skype beta on karmic. No matter what input level I had selected before starting skype, when I attempted to do a first call, skype would mute the mic on my thinkpad t60. This is the mic that's built in on the laptop. I would have to quit that call and then go back to sound preferences and input and sure enough it had reset the levels down to a point where the person I am skyping could not hear me. I would then reset the input level up higher and all would be fine. This happened each and everytime to me on calls on skype. Never happened on Jaunty. I am wondering if this is because of the change to the sound drivers and no choice as before with pulseaudio.

The onboard mic on this laptop has always been found and used correctly; its just getting there with skype was a journey of choosing different drivers for each sound card element. That's all gone now and one only gets pulseaudio the way it appears.

---

### Post by hanzomon4 on 2009-10-24
Same issue... I unticked "skype manage volume" thing as a kinda work around

---

### Post by huzefa.mansoorali on 2009-10-24
I tried following fix, still not working

*
The fix is listed at the bottom under Some Issues and I'd missed it before. Note that the mic is not listed as a problem for this fix on the web page. The problem was listed as quiet speakers which wasn't my issue. Anyways, I tried the fix and it worked for the mic issue. 

1. Simply insert this line at the end of the 
/etc/modprobe.d/alsa-base    file.

options snd-hda-intel model=acer

2. Reboot and open your Gnome Volume Control. Your options will be different than they were before. Play with them until you can get the mic to start recording. I don't remember exactly what my settings were, but it only took about 2 minutes to get the settings right.
*

Huzefa

---


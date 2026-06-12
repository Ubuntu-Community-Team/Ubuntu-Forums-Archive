---
title: "Muting and Sound"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by schroeder719 on 2011-10-13
In 11.04 I had written an upstart script to mute the audio automatically on boot. It would trigger on alsa-restore (stopped) and would just use alsamixer to set Master to mute.
I've noticed that this doesn't work in 11.10, or I should say, I think something else is happening after I log in to unmute it. The audio appears to be muted in lightdm but as soon as I log in it's no longer muted! This is really frustrating. 

Does anyone know why audio would be getting unmuted or alsa-restore would run again after log in?


Thanks,
Andrew

---

### Post by David006 on 2011-11-09
I have the same / opposite issue.

I have several PC, under Ubuntu 11.10 (Oneiric), that I want to have sound.  They start with the boot-up sound, but stubbornly start the desktop with sound muted.

The command '**sudo alsactl store**' doesn't work. (or is over-written).

I am reading up on 'Upstart' ..

---

### Post by David006 on 2011-11-17
see also:

speaker trouble after update to 10.04 (dell inspiron 1545)
[http://ubuntuforums.org/showpost.php?p=11464210](http://ubuntuforums.org/showpost.php?p=11464210)

Mixer always mute after reboot
[http://ubuntuforums.org/showpost.php?p=8358556](http://ubuntuforums.org/showpost.php?p=8358556)

---


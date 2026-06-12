---
title: "Is pulseaudio for all Ubuntu, or just Gnome?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cantab on 2009-10-27
Is pulseaudio being used in all Ubuntu Karmic versions, or the the 'regular', Gnome one?

---

### Post by Brandon Williams on 2009-10-27
I can't comment on whether it is part of a fresh Xubuntu install since I upgraded. I can say, however, that pulseaudio is incompatible with some other parts of the Xubuntu desktop related to audio, namely xfce4-mixer and xfce4-volumed. If pulseaudio _is_ installed as part of a fresh Xubuntu install, it should be removed and a bug should be filed.

---

### Post by slakkie on 2009-10-27
It is designed to be for all of Unix, it runs also on Windows..

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by slakkie on 2009-10-27
> **Brandon Williams said:**
> I can't comment on whether it is part of a fresh Xubuntu install since I upgraded. I can say, however, that pulseaudio is incompatible with some other parts of the Xubuntu desktop related to audio, namely xfce4-mixer and xfce4-volumed. If pulseaudio _is_ installed as part of a fresh Xubuntu install, it should be removed and a bug should be filed.

Try to use the esdcompat, see also: [http://ubuntuforums.org/showthread.php?t=1039173](http://ubuntuforums.org/showthread.php?t=1039173)

---

### Post by slakkie on 2009-10-27
-double-

---

### Post by cantab on 2009-10-27
> **slakkie said:**
> It is designed to be for all of Unix, it runs also on Windows..

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

Yeah, it's designed for that. What I mean is, if I do a fresh install of Xubuntu or Kubuntu Karmic, will it use pulseaudio? If I do an install of $other_distribution, using Gnome as the desktop, is THAT likely to use pulseaudio?

---

### Post by buzzmandt on 2009-10-27
friend of mine just did a fresh install of kubuntu, it had pusleaudio on her system but wasn't set to be used as the first "preferred" option.  I've been running pulse on my kubuntu since alpha 1 and haven't had any trouble from it.  In fact, teamspeak for linux which is notorious for using oss and killing all other sound while it's running runs fabulous and all other sounds work at the same time.  

as for the other q's couldn't help ya on those.

---

### Post by Brandon Williams on 2009-10-27
> **slakkie said:**
> Try to use the esdcompat, see also: [http://ubuntuforums.org/showthread.php?t=1039173](http://ubuntuforums.org/showthread.php?t=1039173)

The only problem with pulseaudio in XFCE is that, at startup, xfce4-volumed and xfce4-mixer somehow manage to mute the sound when pulseaudio is running. Pulse was being started from somewhere in my xfce session, but I couldn't figure out where it was coming from (/etc/X11/Xsession.d/70pulseaudio doesn't look like it should start it; there no associated .desktop in /etc/xdg/autostart or ~/.config/autostart). Purging pulseaudio was the only way I could find to solve the problem.

I'll look into esd again if I decide that it's important to me.

---

### Post by Brandon Williams on 2009-10-27
Another interesting point is that, according to the various scripts and config files that are installed as part of pulseaudio, the pulseaudio server _should_ only be started if gnome-session is your session startup program. There may be a script installed by kubuntu that ensures that it also is started for KDE, but there is no such startup code installed by xubuntu. As far as I can tell, pulseaudio should not be running within an xfce session, even if it is installed. And yet it is ...

---


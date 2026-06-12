---
title: "No sound in firefox aka YouTube"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by techdude3177 on 2009-02-15
I upgraded pulse audio today and i am no longer getting audio through firefox even if i run the killall pulseaudio command.
bummer

but still getting audio through the mp3 player

---

### Post by Vardaan Aggarwal on 2009-02-15
may be there is a problem on your music system .

---

### Post by techdude3177 on 2009-02-15
when i was running 8.10 when it was in beta i was missing a package for flash audio but i forget what that package was.
but that doesnt seem to be the issue

---

### Post by techdude3177 on 2009-02-16
:lolflag: got it! upgraded to Flash 10, doesnt like Flash 9 for whatever reason.

---

### Post by Sspankyy on 2009-02-16
I've got the same problem... It started today...  I've got Flash 10, so I'm not sure if I should Downgrade to 9 or what....

Well, Any suggestions?

Scott

---

### Post by techdude3177 on 2009-02-16
try uninstalling flash and then get the new one from here [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by Sspankyy on 2009-02-16
I Uninstalled Flash, then I downloaded it from the link, reinstalled it, tried Youtube... Nothing, ubuntu then prompted me to update my flash to a newer version, so I did, still nothing...

Also, just so you don't ask, Yes, my volume is up....

Scott

---

### Post by techdude3177 on 2009-02-16
:confused:

---

### Post by Sspankyy on 2009-02-18
OK, so for no good reason, it just started working again.

This is not the first time this kind of thing has happened, and each time it happens I really wonder if my friends who think Linux is full of pixies and gremlins fighting over my computer are right...

Just a thought, haven't had enough coffee yet... so my thoughts are not good yet..

Scott

---

### Post by Committed on 2009-02-18
Same problem here and it's getting downright discouraging.  Sound sometimes in all apps, sometimes only system sounds, sometimes sound just quits but comes back with reboot.  Was just watching a youtube video and sound just cut out half way through. Arrgghh!!!!

If I can't solve this once and for all, I will be forced to go back to windoze.

---

### Post by taavikko on 2009-02-18
> **Committed said:**
> Same problem here and it's getting downright 
If I can't solve this once and for all, I will be forced to go back to windoze.

Yep... just use operating system running alpha-status...

---

### Post by darkerlink on 2009-02-21
use alsa mixer. Go to System>Preferences>Sounds and select your sound card(if you have 2) and make sure it has "Alsa" on it somewhere. Then uninstall pulseaudio with 

sudo apt-get remove pulseaudio

That should work since I had the exact same problem!

---

### Post by ugkbunb on 2009-02-21
I had this same problem... all though it is not the recommend way to run pulseaudio it fixed all my issues with no sound on startup. If you are on a single user linux box then imho there is only benefits from running it at the system-wide level

/etc/pulse/daemon.conf 
daemonize=yes
system-instance = yes 

/etc/default/pulseaudio 
PULSEAUDIO_SYSTEM_START=1

I also changed the following in daemon.conf - I believe this fixed my issues with scratchyness

resample-method = src-sinc-best-quality (i set it to the highest,,, change it to what you want it)
high-priority = yes 
nice-level = -11
default-fragments = 5
default-fragment-size-msec = 25

Also I set the following to the best (also highest cpu)...
resample-method = src-sinc-best-quality 

from best to worst the options are:
src-sinc-best-quality, src-sinc-medium-quality, src-sinc-fastest, speex-float-{10-0}, speex-fixed-{10-0}, ffmpeg, src-zero-order-hold, src-linear, trivial

---


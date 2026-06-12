---
title: "Sound muted on Karmic by default"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wpshooter on 2009-09-08
When installing Karmic, the sound is MUTED by default.

Why is this ?

Thanks.

---

### Post by MRGt on 2009-09-08
Maybe is the same problem that i have in Jaunty a week ago, is about the war betwen alsa & pulseaudio.

The solution for me was purge pulseaudio, but try googling to find the best solution for you.

---

### Post by zika on 2009-09-08
I've solved that problem by installing padevchooser ... If You need more details just ask ...

---

### Post by andrewabc on 2009-09-09
> **wpshooter said:**
> When installing Karmic, the sound is MUTED by default.

Why is this ?

Thanks.

Maybe it was to fix the bug where volume was turned up all the way and scared anyone testing it? :P

---

### Post by Vaun on 2009-09-09
I would highly recommend testing the Ubuntu Dev Audio PPA. This is the first time in the cycle my sound had not been muted on start up from reboot from the recent updates.

```
deb http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu karmic main
```

---

### Post by drs305 on 2009-09-09
> **Vaun said:**
> I would highly recommend testing the Ubuntu Dev Audio PPA. This is the first time in the cycle my sound had not been muted on start up from reboot from the recent updates.

```
deb http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu karmic main
```


Gave me a chance to try out Karmic's new "add-apt-repository" command. Added it automatically to /etc/apt/sources.list.d and imported the public key. 

```

sudo add-apt-repository ppa:ubuntu-audio-dev

```
Worked great. Thanks for the info.

---

### Post by ktp on 2009-09-09
> **MRGt said:**
> Maybe is the same problem that i have in Jaunty a week ago, is about the war betwen alsa & pulseaudio.

The solution for me was purge pulseaudio, but try googling to find the best solution for you.

I have found that if pulseaudio dies and restarts, on next restart the volume will get muted.  I was able to verify this in Jaunty by sudo killall pulseaudio and restarting the system.  After killall but before restart, audio will work correctly with correct volume level.  But after restart, volume would be muted.

---

### Post by kozimodo on 2009-09-10
Purging pulseaudio also did the trick for me.

---

### Post by madmetal on 2009-09-10
i have the same problem , plus i have no sound at mic input..

---

### Post by madmetal on 2009-09-10
> **drs305 said:**
> Gave me a chance to try out Karmic's new "add-apt-repository" command. Added it automatically to /etc/apt/sources.list.d and imported the public key. 

```

sudo add-apt-repository ppa:ubuntu-audio-dev

```
Worked great. Thanks for the info.

didn't solve the problem for me..
if i purge pulseaudio will it affect my system ?

---

### Post by drs305 on 2009-09-10
> **madmetal said:**
> didn't solve the problem for me..
if i purge pulseaudio will it affect my system ?

madmetal,

Sorry if I gave a false impression. I just tested out installing the ppa. I haven't removed PA. From time to time my PA fails but a "killall pulseaudio" allows it to resume after a short period.

---

### Post by Vaun on 2009-09-10
Same here.  I just rebooted again and the sound was muted.

I have to run ```
killall pulseaudio
``` sporadically to restore my sound when switching sound applications, Banshee, Rhythmbox, etc. along with using the freedesktop sound theme which incporporates many more sounds.  It has become less frequent that I have to kill the process as it was towards the beginning of the cycle.

---


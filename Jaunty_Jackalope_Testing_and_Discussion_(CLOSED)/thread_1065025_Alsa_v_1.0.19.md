---
title: "Alsa v 1.0.19"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by minisori on 2009-02-09
I think the .19 version should be included in jaunty, I have been trying this one for a couple of days and i find it to work much better than the current version in jaunty. It fix various annoying bugs, like now it mutes the speakers when i plug the headphones and such things. But the most important the audio over hdmi now works without problem with my nvidia 9600gt, and probably with many more.

Here are the many changes over 1.10.18:
[http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.19](http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.19)

---

### Post by jfernyhough on 2009-02-09
Is there a PPA for this somewhere? (just to make it easier :D)

---

### Post by plun on 2009-02-09
> **jfernyhough said:**
> Is there a PPA for this somewhere? (just to make it easier :D)

I have not found it anyway....

Alsa add this to your "she bang" party....:-\"

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html)


I have the same opinion as OP about this....  BUT where is Debian :confused:

---

### Post by minisori on 2009-02-09
I have not found any ppa, but just tried this script, made by soundcheck, and works and is pretty easy.

[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+hdmi)

---

### Post by pferraro on 2009-02-09
> **jfernyhough said:**
> Is there a PPA for this somewhere? (just to make it easier :D)

[https://launchpad.net/~pgquiles/+archive/ppa](https://launchpad.net/~pgquiles/+archive/ppa)

---

### Post by techdude3177 on 2009-02-09
> **minisori said:**
> i think the .19 version should be included in jaunty, i have been trying this one for a couple of days and i find it to work much better than the current version in jaunty.

+1

---

### Post by plun on 2009-02-09
Just a little notification....  if I knows jfernyhough correct.

It will be both Alsa and PA...:D
> 
Colin Guthrie already pointed out that m**odule-positional-event-sounds is completely borked**. So, while testing make sure not to load it
otherwise volumes of all your streams might start moving in strangest
ways as if controlled by some ghost. [B]It is loaded by default though,
hence you need to manually disable it[/B].

```

gksudo gedit /etc/pulse/default.pa
```


./bootstrap.sh > make > sudo make install

:guitar:

---

### Post by minisori on 2009-02-09
Good a ppa, much better, thx :D

---

### Post by plun on 2009-02-09
> **minisori said:**
> Good a ppa, much better, thx :D

Nothing is built with Jauntys environment....:-k

---

### Post by PRGUY85 on 2009-02-09
Will this release finally add full support for X-FI now that the driver code was made public by Creative?

---

### Post by plun on 2009-02-09
> **PRGUY85 said:**
> Will this release finally add full support for X-FI now that the driver code was made public by Creative?

Nope.... The Alsa guys didn't include X-Fi for unknown reasons with ver 1.0.19.


EDIT


> [http://www.phoronix.com/scan.php?page=news_item&px=NzAwMw](http://www.phoronix.com/scan.php?page=news_item&px=NzAwMw)

While Creative Labs had allowed 4Front Technologies to create open-source X-Fi support in the Open Sound System nearly a year ago by releasing the needed APU specifications, **there still is no Creative X-Fi support in ALSA 1.0.19.** Creative Labs had even open-sourced their X-Fi driver back in November, but no code has yet to hit ALSA. 



---

### Post by PRGUY85 on 2009-02-09
This is still the reason I haven't fully switched to Ubuntu.  Win 7 just works better with my hardware at the moment.

---

### Post by taavikko on 2009-02-09
> **PRGUY85 said:**
> This is still the reason I haven't fully switched to Ubuntu.  Win 7 just works better with my hardware at the moment.

Yes, when vendors release buggy code, it's ALSA's problem...;)
Just like nVidia releases buggy code, it's Distro's problem...

---

### Post by PRGUY85 on 2009-02-09
Man, I love Ubuntu/Linux as much as anyone here.  And I know that Creative hasn't been great with our community.  Yet, I have their hardware because it is a good product.  Also, one of the main points of Linux at the moment is its hardware compatibility so I find it appropriate to just ask for it to be compatible with Creative too now that they released the driver code.

---

### Post by plun on 2009-02-10
> **PRGUY85 said:**
> This is still the reason I haven't fully switched to Ubuntu.  Win 7 just works better with my hardware at the moment.

Well.. If you have missed it.

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

The driver just works with minimal work.  Just a few copy and paste..:guitar:

---

### Post by Nullack on 2009-02-10
> **taavikko said:**
> Yes, when vendors release buggy code, it's ALSA's problem...;)
Just like nVidia releases buggy code, it's Distro's problem...

Sorry. but thats nonsense.

Linux has a broken audio stack. It also has a broken graphics stack. Ontop of the architectural things missing, there is missing features in audio and graphics that is very much needed for a complete desktop OS.

Being enthusiastic is good about Linux, but when people become delusional from the reality of what Linux is it doesnt help the community. These things will be fixed in time I'm sure, but they aint here now.

---


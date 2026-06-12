---
title: "Can I safely upgrade the kernal in my situation?"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by JS Lemming on 2007-10-05
A few weeks ago I upgraded the kernal to 2.6.20-16.31 as suggested by the Update manager. However, it broke my system pretty good. So I started booting from the old "15" kernal. When I first installed ubuntu fiesty long ago I had to compile some ALSA stuff in order to get the sound working. And after upgrading to "16" I had to compile the stuff again even though I was booting into the old "15".

Now Update Manager has a new version of the "16" kernal for me. So my question is, if I update this 16 (just to get rid of the annoying "The are # upgrades available" thing), will it leave my "15" untouched that I have no problems using? Or will it mess everything up again and make me redo ALSA compilation even in "15".

I know that's probably confusing as heck but I'm not good with words.

PS: if you think I should upgrade... should I boot into the broken 16 to do it or my 15?

Thanks.

---

### Post by Xavier Oddmon on 2007-10-05
Was alsa the only problem? My sound barely worked after upgrading to kernel 16, it kept choosing my non-existant integrated audio card as default (despite my telling it otherwise countless times). If this is the only problem, try disabling the integrated sound card in BIOS, boot ubuntu, and see if you have sound. (You may have to do some tweaking afterwards, but it's nothing difficult, and i'm certainly no expert)

---

### Post by trippinnik on 2007-10-05
If 15 is working, why upgrade?  You can use sudo aptitude hold <package> to put a hold on it.

---

### Post by JS Lemming on 2007-10-05
I have tried putting it on hold... or holding them back, whatever it's called. But they still show up in Update Manager wanting me to upgrade.

---

### Post by rsambuca on 2007-10-05
Try using Synaptic - select the linux-image you want to keep using, and go to the top and select "Package -> Lock Version".  I think it should then ignore any updates for that.

---

### Post by JS Lemming on 2007-10-06
That didn't work either.

---

### Post by Pumalite on 2007-10-06
Stick to a working system and ignore the 'pink' square until you are ready to save your data and do a clean install. In ten days maybe?

---

### Post by JS Lemming on 2007-10-06
So the gutsy release is in 10 days? Cause that would be a good time.

---


---
title: "Sound Popping / Pipping Intel Corporation 82801H"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vixsandlee on 2009-10-22
Hiya,

I upgraded from 9.04 yesterday and since then I have been getting random popping / pipping from the speakers (even if I mute the system)

It sounds like it is re-starting the sound system.

If I remove alsa it stops, and then it restarts when I reinstall the sound system.

So I figure its sound related.

alsa info output is here

[http://www.alsa-project.org/db/?f=1bcee026df1d5b946e1b4077871950789af27b32](http://www.alsa-project.org/db/?f=1bcee026df1d5b946e1b4077871950789af27b32)

dont know what other info you need, but just let me know.

cheers.

---

### Post by FIONEX on 2009-10-22
I hear it too!!!
It's damn annoying every time there's a sound played. I have a HP Pavilion TX 2500 series laptop.  I have hda_intel sound.  I wonder what the problem is.

---

### Post by the.lost.one on 2009-10-22
Oh yea. I hear that too. I have HP Pavilion DV6000 series laptop. I have altec lansing speakers built in and my sound card should be this:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by cyberkilla on 2009-10-22
Hello, I had the same problem:

[http://ubuntuforums.org/showpost.php?p=8097391&postcount=5](http://ubuntuforums.org/showpost.php?p=8097391&postcount=5)

You just need to put a # at the beginning of the line that looks like: "**options snd-hda-intel power_save=10**", which is at the end of "**/etc/modprobe.d/alsa-base.conf**".

Worth a try - it worked for me and others.

---

### Post by vixsandlee on 2009-10-23
Hp here too, 

Have tried what you said cyberkilla, going to restart now and cross everything :D

At least its not just me though.

---

### Post by vixsandlee on 2009-10-23
Wooo yay it worked.


Thanks :)

---

### Post by cyberkilla on 2009-10-23
> **vixsandlee said:**
> Wooo yay it worked.


Thanks :)

No problem:P It's just a shame that nobody has bothered to fix the issue properly yet. It has been known for a good few weeks now, and I'm sure I've seen a bug report or two about it.

---

### Post by chriswyatt on 2009-10-23
Same here, but I have a slightly different soundcard:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've also been having distortion, anyone else been having the same issue?

[http://ubuntuforums.org/showthread.php?p=8153357](http://ubuntuforums.org/showthread.php?p=8153357)

---

### Post by FIONEX on 2009-10-24
Uhhh well I hope that battery life isn't utterly important for you.  It seems to me that you are sacrificing power consumption by not allowing linux to suspend the sound card when it's not being used.  The bug needs to be addressed in the driver source rather than disabling suspend all together.  This will do in the meantime.

I used to love linux because it was screaming efficient resource management, speed, and power.  With the release of Windows 7, I've been booting linux less often. What drives me away from linux is stupid bugs like this.  It's always about sacrificing some hardware functionality.  Windows 7 bolsters fast boot, low memory consumption, and a recently implemented powershell that needs to improvement.  Since my university provides Win 7 for free, linux really has no obvious advantage.  I'll keep my linux kuz it'll be my customized environment.

---

### Post by cyberkilla on 2009-10-24
> **FIONEX said:**
> Uhhh well I hope that battery life isn't utterly important for you.  It seems to me that you are sacrificing power consumption by not allowing linux to suspend the sound card when it's not being used.  The bug needs to be addressed in the driver source rather than disabling suspend all together.  This will do in the meantime.

I used to love linux because it was screaming efficient resource management, speed, and power.  With the release of Windows 7, I've been booting linux less often. What drives me away from linux is stupid bugs like this.  It's always about sacrificing some hardware functionality.  Windows 7 bolsters fast boot, low memory consumption, and a recently implemented powershell that needs to improvement.  Since my university provides Win 7 for free, linux really has no obvious advantage.  I'll keep my linux kuz it'll be my customized environment.

Lol.

Of course it should be fixed, but I'm not holding my breath.

Also, it's worth remembering that the card going to sleep seems like a new trick, as the line was added the the .conf only a few weeks ago, and it only seems to be for hda-intel cards/codecs/whatever.

---

### Post by amano on 2009-10-24
> **chriswyatt said:**
> Same here, but I have a slightly different soundcard:

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've also been having distortion, anyone else been having the same issue?

[http://ubuntuforums.org/showthread.php?p=8153357](http://ubuntuforums.org/showthread.php?p=8153357)

I have two boxes. My brand new ASRock ION 330 (Atom 330 proc + Nvidia ION chipset including a via sound chip) has the pops. 

The old P4 2.800 with its creative sound blaster live 5.1 has this metallic ratlle snake hiss. That combo worked fine before. I have never had issues with pulseaudio from the beginning with it up until recently.

I hope crimsun has some magic patch up his sleeves to fix at least the pops as they seem to be more common. Although a sound blaster isn't such a rare sound card...

---


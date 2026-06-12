---
title: "Volume control won't work on Hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by tzg6sa on 2008-04-26
Hi!

I've just installed the Hardy Heron. The Volume Control on the top right corner won't work. I mean, if I move the slide for example to 40% it jumps back to 100% immediately. Another value can not be set. It's a bit frustrating, cause the sounds are unbearable.
Do you have some ideas to solve the issue?

Zoli

---

### Post by tzg6sa on 2008-04-27
Has anybody the same problem?

---

### Post by russo.mic on 2008-04-27
> **tzg6sa said:**
> Has anybody the same problem?

What kind of audio hardware are you using?  Have you checked the sound properties and/or alsamixer to make sure the binding is correct?  

Russo

---

### Post by tzg6sa on 2008-04-27
I have used the autodetect option and ALSA and OSS for playback and mixing (in all field in the preferences/Sound/Devices).

To be honest, I have no idea why can not be modify the value of volume in any set-ups. Why is there this option then?!? (Pleas don't answer this question, solving the problem would be more appreciated :) )

---

### Post by russo.mic on 2008-04-27
> **tzg6sa said:**
> I have used the autodetect option and ALSA and OSS for playback and mixing (in all field in the preferences/Sound/Devices).

To be honest, I have no idea why can not be modify the value of volume in any set-ups. Why is there this option then?!? (Pleas don't answer this question, solving the problem would be more appreciated :) )

Are you asking why you can't bind the volume keys to another value?  because you can...in the same dialog.

Russo

---

### Post by tzg6sa on 2008-04-29
I want to change the system volume, because 100% is too much. The trivial solution would be to change it by clicking on the speaker icon on the top right corner (on GNOME). I would like to do it, but I can't. Not because I am a stupid (but who knows...), I can't do it, because it won't change. The value stays (it jumps back immediately). I don't know the reason, I havn't found any answers in the forum or in google.

I havn't got any problem on 7.10 and 7.04. That's why is it bothering me so much.

Zoli

---

### Post by wolfydRg on 2008-04-29
In my case the volume can be adjusted but at next restart is loaded default at 100%. I use OSS mixer and ESD because i have NVidia Nforce2.

The setting for save volume ...
/usr/bin/nvmix-reg -f /etc/nvmixrc -S
and load volume ...
/usr/bin/nvmix-reg -f /etc/nvmixrc -L
 .... works, but at the end at restart is loaded at 100%.

---

### Post by tzg6sa on 2008-05-12
I have "ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)".

I played again with the set-up but I can't manage to scale the volume. I have recognized, that I can mute it, but this 1 bit resolution is not what I would like.
Any idea how to debug it? The sound card works, I am just not able to lower the volume from 100%.

Thanks!
Zoli

---

### Post by tzg6sa on 2008-05-12
The solution:
[http://ubuntuforums.org/showpost.php?p=4675505&postcount=8](http://ubuntuforums.org/showpost.php?p=4675505&postcount=8)

---

### Post by jallosway on 2008-05-13
Hi everyone!

I've got the same problem with my volume control. When I boot or reboot it's reset to 100%. But when I changed device from "[COLOR="Red"]0: CA0106 (Alsa Mixer)[/COLOR]" to "[COLOR="Red"]2: PulseAudio ALSA PCm on front:0 (CA0106) via DMA (PulseAudio Mixer)[/COLOR]" the problem disappeared. So that's one problem solved.

The next problem, which actually is my primary problem, is that I don't have any sound at all. I have a Creative Soundblaster X-fi Extrem Audio but have not installed the driver for my Ubuntu (Hardy x64). I have downloaded the "[COLOR="Red"]XFiDrv_Linux_US-1.18[/COLOR]" driver from Creativ's web page. I would appreciate any help on how to install it and if necessary configure it once installed.

Maybe this is the wrong thread? In that case, then perhaps someone can help me find the right one?

Many Thanks, Jallosway

---

### Post by tzg6sa on 2008-06-18
Somebody told me, that he uses the "sudo alsa force-reload" command, but I'm not sure, that he has not the same problem I think, but the solution sames like the same, albeit I don't now the diference between the commands...
I posted it here for the sake of documenting the idea.

---

### Post by ckoester on 2008-06-24
I can confirm the same problem on an HP Compaq dx2200 Microtower with a fresh Hardy Heron install.

The volume control applet near the clock was stuck at 100% and I could not drag it at all.  Sound did work, but it was maxed out at 100%.

The fix that tzg6sa linked to in post #9 worked for me.  Here's the link again:

[http://ubuntuforums.org/showpost.php?p=4675505&postcount=8]("http://ubuntuforums.org/showpost.php?p=4675505&postcount=8")

---

### Post by tzg6sa on 2009-04-22
The link is dead. Could somebody fix it?

---

### Post by ckoester on 2009-04-22
I submitted the broken link to the site administrator.

---


---
title: "Latest totem upgrades --&gt; Video thumbnailer broken?"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Toe on 2009-06-03
Today Totem was updated to version 2.27.1-1ubuntu1.

Since then video thumbnailing in Nautilus has stopped working.

The problem seems to be limited to videos. Thumbnailing of pictures still works fine.

Can anybody confirm this issue?

---

### Post by davideotape on 2009-06-03
Sorry, all working fine for me over here :(

---

### Post by super.rad on 2009-06-03
Yup video thumbnails aren't working and if I try to open totem I get
> Could not launch 'Movie Player'
Failed to execute child process "totem" (No such file or directory)

Bug report filed [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/383187](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/383187)

---

### Post by psyke83 on 2009-06-03
> **super.rad said:**
> Yup video thumbnails aren't working and if I try to open totem I get


Bug report filed [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/383187](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/383187)

Reinstalling the totem package (which wasn't removed, oddly) fixes it:
```
$ sudo apt-get install --reinstall totem
```

Not sure why this is necessary, though...

---

### Post by davideotape on 2009-06-03
Hmm, reloading synaptic now to see if I missed an update.

EDIT: Downloading latest gnome updates


EDIT 2: Installing latest gnome updates

EDIT 3: I have the same problems. Can't even double click to open now.Downloading

---

### Post by super.rad on 2009-06-03
> **psyke83 said:**
> Reinstalling the totem package (which wasn't removed, oddly) fixes it:
```
$ sudo apt-get install --reinstall totem
```Not sure why this is necessary, though...

Totem now opens but video thumbnails still don't work for me

---

### Post by davideotape on 2009-06-03
Filed upstream bugreport and confirmed original report. I'll refrain from re-installing so I can still reproduce the problem

---

### Post by davideotape on 2009-06-03
Bizzare, running ```
totem %U
``` from the command line gives me this: ```
tdavid@david-desktop:~$ totem
The program 'totem' can be found in the following packages:
 * totem-gstreamer
 * totem-xine
Try: sudo apt-get install <selected package>
bash: totem: command not found

```

---

### Post by 23meg on 2009-06-03
Due to a change coming from Debian, the *totem* package is calling "update-alternatives --quiet --remove-all totem || true" in postinst, to clean up the alternatives, and that's ending up deleting the binary. Doing this in preinst will fix the issue and the Debian maintainer is notified, so just wait.

---

### Post by davideotape on 2009-06-03
> **23meg said:**
> Due to a change coming from Debian, the *totem* package is calling "update-alternatives --quiet --remove-all totem || true" in postinst, to clean up the alternatives, and that's ending up deleting the binary. Doing this in preinst will fix the issue and the Debian maintainer is notified, so just wait.

Thanks for the quick reply ;) Seems I was a bit too eager in reporting the bug upstream :(

---

### Post by 23meg on 2009-06-03
> **davideotape said:**
> Thanks for the quick reply ;) Seems I was a bit too eager in reporting the bug upstream :(

You reported it in the GNOME bug tracker? Please refrain from that unless you're fairly sure the issue is based on the upstream code rather than the Ubuntu packaging or integration. This is obviously a packaging issue so it's something that definitely shouldn't be reported upstream.

---

### Post by geojorg on 2009-06-03
I have a different bug, when i open totem in fullscreen my system reloads to the login screen, does anyone has the same problem ? Can someone try to reproduce the bug.

---

### Post by super.rad on 2009-06-04
Was watching videos in totem full screen yesterday after the updates with no problems. File a bug on launchpad about it

---

### Post by geojorg on 2009-06-04
I found the bug in launchpad is only for intel users.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/383129](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/383129)

---

### Post by Nullack on 2009-06-04
Gday folks :) As a tip, I find asking the dev in question whos working on the package if its an upstream issue if your not sure. Its really great to engage upstream but we should be pretty certain before engaging upstream.

---

### Post by psyke83 on 2009-06-04
> **Nullack said:**
> Gday folks :) As a tip, I find asking the dev in question whos working on the package if its an upstream issue if your not sure. Its really great to engage upstream but we should be pretty certain before engaging upstream.

I would imagine that upstream would get annoyed to have so many false-positives from downstream sources, though. I think it's better to tell all users to report their bugs in Ubuntu to Launchpad. When the bug is triaged by someone more knowledgeable, they can decide whether to forward it upstream or not...

---

### Post by Nullack on 2009-06-05
I think you misunderstand mate. LP has the ability for the existing LP bug to be linked to upstream as a bugwatch tracker. Once a dev has confirmed its an upstream problem, it helps formalise the entry with watching the upstream bug report and also saves the dev time on our end. As I said, if your not sure if its upstream or not, ask a dev. Quite often for example Sebastien has confirmed its upstream and Ive setup a bugwatch upstream and an upstream bug, which saves him time.

---

### Post by psyke83 on 2009-06-05
> **Nullack said:**
> I think you misunderstand mate. LP has the ability for the existing LP bug to be linked to upstream as a bugwatch tracker. Once a dev has confirmed its an upstream problem, it helps formalise the entry with watching the upstream bug report and also saves the dev time on our end. As I said, if your not sure if its upstream or not, ask a dev. Quite often for example Sebastien has confirmed its upstream and Ive setup a bugwatch upstream and an upstream bug, which saves him time.

Sure, I get what you mean. I meant that inexperienced users shouldn't *file* an upstream bug when they encounter an issue (especially with the development release). However, if they find a matching upstream bug that already exists, they should associate it with their Launchpad bug, of course.

---

### Post by Edgar09 on 2009-06-25
Totem has started to be a great solution & now it all just a big mess.!!

But i found a better & more suitable Player..

It's the VLC media player..

It's way better..

Sorry Totem lovers...

But i got a new love...

---


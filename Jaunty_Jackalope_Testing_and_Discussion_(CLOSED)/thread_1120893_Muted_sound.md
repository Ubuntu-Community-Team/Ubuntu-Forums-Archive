---
title: "Muted sound?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by m-tarek on 2009-04-09
Hi,\\:D/
I had a problem with 8.10 that the sound was crackling or something like noise.#-o
But when I installed Jaunty, the whole problem seemed to be solved but the sound was muted now.
I'm using ALSA and I think that the problem was from pulseaudio.
I tried to use alsamixer on terminal but I found it on the highest level. I have HP laptop and my card is snd-hda-intel.
[-o<PLEASE HELP ME[-o<

---

### Post by kansasnoob on 2009-04-09
Click on the volume applet and see if the Master Volume is muted.

You may be able to tell even if there's just a red X thru the applet.

If you find that it mutes every time you restart it may be this bug:

[https://bugs.launchpad.net/ubuntu/+bug/357833](https://bugs.launchpad.net/ubuntu/+bug/357833)

---

### Post by m-tarek on 2009-04-09
No I looked at the appalet first then i tried alsamixer

---

### Post by m-tarek on 2009-04-09
And i thing that my problem is not like the bug on lauchpad.

---

### Post by kansasnoob on 2009-04-09
First of all, have you run in terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

since upgrading to Jaunty? If not do so now. If you still have NO sound and no red-X thru the volume applet do the following:

Go to terminal, run the following commands and post the full output here:

```
aplay -l
```

```
find /lib/modules/`uname -r` | grep snd
```

```
lspci -v | less
```

---


---
title: "Ubuntu 20.04 Nvidia drivers not working."
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by rytis2002 on 2020-06-12
Hello, my nvidia drivers are broken and only the display(I think) uses the card...
I have tried a lot of techniques but with no luck...
My pc is NP550P5C I am running "Linux rytuks-550P5C-550P7C 5.4.0-37-generic"
There was always this problem, but ten I didn't need the gpu, and its rendering(OpenGL) fetures.
Reinstalling doesn't work.
Different versions of drivers also seem not to work and if i install some, they become 390 again.

```
rytuks@rytuks-550P5C-550P7C:/usr/lib/nvidia$ nvidia-settings 

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:57672): GLib-GObject-CRITICAL **: 00:10:05.218: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 00:10:05.221: PRIME: Requires offloading
** Message: 00:10:05.221: PRIME: is it supported? yes
** Message: 00:10:05.257: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query
** Message: 00:10:05.258: PRIME: on-demand mode: "1"
** Message: 00:10:05.258: PRIME: is "on-demand" mode supported? yes

```
and the Nvidia bug thing [https://gist.github.com/rytis2002/a0dc2c25b78ce0b4ce697e7a67c47c29](https://gist.github.com/rytis2002/a0dc2c25b78ce0b4ce697e7a67c47c29)
I want to simply get my gpu to render openGL and not my intel HD graphics.
i have tried "prime-select nvidia" but it does nothing

---

### Post by rytis2002 on 2020-06-12
forgot to mention that i have tried prime-select nvidia but it does nothing

---

### Post by CatKiller on 2020-06-12
418 is the last branch that supports your GT 650M, so there's no point trying to install anything later than that. If you have a driver package already installed you need to purge it before you install a driver from a different branch, otherwise it won't work. Optimus is also a general pain.

---

### Post by rytis2002 on 2020-06-13
If I try to purge 390 and install 418 after the reboot nvidia drivers are never found by the system and screen resolution is decreased drastically, then I do ```
sudo rm -v /etc/X11/xorg.conf*
```, reboot, and everything is back to normar, but my driver shows up as 390(Like a ghost XD).

Now, after I purged everything the driver 390 stays...
Oh, it was the Xorg driver, my bad.

In the additional drivers it only shows 3 options:
390
340
Xorg

418 is not an option and if I try to install it from the nvidia site, it fails  [URL="https://pastebin.com/W4cARBSb"]https://pastebin.com/W4cARBSb
[/URL]nvidia-settings have never worked for me, not even once...

---

### Post by rytis2002 on 2020-06-13
OK so I finally got it to work, by uninstalling libgl1 and reinstalling it, idk why it worked... reinstalling billions of times and testing different solutions didn't seem to work...

---


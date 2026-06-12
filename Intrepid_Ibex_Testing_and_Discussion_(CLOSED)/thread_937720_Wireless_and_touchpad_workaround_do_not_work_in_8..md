---
title: "Wireless and touchpad workaround do not work in 8.10"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vegetali on 2008-10-04
Hi
 I have just fresh-installed Intrepid Ibex beta on a macbook santarosa v3, as I do not use it as production machine. In the following I refer to workarounds explained here
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

-Sound worked straight out of the box (although it muted by itself a couple of times, but it was back after rebooting, I even did not open volume control).

-xorg.conf has changed a lot since 8.04. It seems that the X server configures everyting by itself, and there is not much left in xorg.conf. I do not know how to apply the touchpad trick that made my touchpad work so fine. Namely, touchpad works, multitouch does not (in particular, I do not have right click).

-I installed the wireless driver as explained in the above link. It worked fine with 8.04, but now it seems ubuntu does not detect wireless at all.

If anyone can help, I would be grateful. I think it would be nice to start writing some tips for 8.10 users also.

---

### Post by kosumi68 on 2008-10-04
The synaptics auto-detection is made via hal, and it is possible to add specific settings in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi.

For a traditional /etc/X11/xorg.conf configuration, make sure you have something like this in there:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"

        # simulate middle/right buttons
        Option          "ClickFinger1"  "1"
        Option          "ClickFinger2"  "3"
        Option          "ClickFinger3"  "2"
EndSection

```

Also remember to link the touchpad to your layout like this:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
        InputDevice     "Configured Mouse"
EndSection

```

---

### Post by cyberdork33 on 2008-10-04
There is a bug report on the sound issue:

[https://bugs.edge.launchpad.net/mactel-support/+bug/162347](https://bugs.edge.launchpad.net/mactel-support/+bug/162347)

---

### Post by vegetali on 2008-10-04
Thanks for the replies. Any help for the wireless? Am I the only one with this problem?

For the touchpad: thanks. my do you mean I should actually add that lines to my xorg.conf? At present, the content of my /etc/X11/xorg.conf file is quite short
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
I ll try to add the two boxes above at the file, and see what happens.


For the sound: thx. yes, sound on macbook is a bit buggish. In this post, I wanted also to say that with Ibex is a bit better, as it worked out of the box.

---

### Post by cyberdork33 on 2008-10-04
For WiFi you can try the wl driver...
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

---

### Post by elinhansen on 2008-10-11
How did it go with the wl driver? If you used it.

---

### Post by C38a7r1zvl on 2008-10-12
Hi,

I'm struggeling with proper touchpad functionality as well but getting wifi to work is easy: [https://wiki.ubuntu.com/MacBook/SantaRosa#Wireless%20(Broadcom%20BCM4328)]("https://wiki.ubuntu.com/MacBook/SantaRosa#Wireless%20(Broadcom%20BCM4328)")

---

### Post by wgrant on 2008-10-12
See [the wiki page](https://wiki.ubuntu.com/MacBook/SantaRosa#Touchpad%20(appletouch)) for configuring the touchpad.

---

### Post by C38a7r1zvl on 2008-10-12
Thanks for the pointer, William but I'm actually the author of the linked wiki page and had just figured out how to configure the tp. Now all standing between me and total Intrepid on Macbook bliss are the keyboard's function keys :)

---

### Post by Cifra on 2008-10-27
Please, if anyone found a way to make the touchpad work fully, let us know!

---

### Post by wgrant on 2008-10-27
> **Cifra said:**
> Please, if anyone found a way to make the touchpad work fully, let us know!

I might, if you actually told us what was not fully working about it! I believe I've fixed most configurations, so your complaint lacks information and is useless.

---

### Post by Cifra on 2008-10-27
[http://ubuntuforums.org/showthread.php?t=959740](http://ubuntuforums.org/showthread.php?t=959740)

Here's the thread with my problem. Thanks!

Basically, HAL doesn't change anything - left click still doesn't work.

---


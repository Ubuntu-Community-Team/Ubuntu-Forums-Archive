---
title: "Nvidia X Server Settings issue"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2009-09-23
I am using dual monitors, but I am not able to save any changes to my xorg.conf with Nvidia X Server Settings.

Error:> Failed to parse existing X config file '/etc/X11/xorg.conf' !

If I close the error window the program crash. The "Save to X configuration file" button has never worked for me ever. But I have been able to see the generated xorg config then copy and paste it to the actual xorg.conf. I am not able to do that now...

What should I do? I am tired of only having one monitor working on every startup...

---

### Post by dinxter on 2009-09-23
try
$sudo nvidia-settings --no-config

---

### Post by gjoellee on 2009-09-23
> **dinxter said:**
> try
$sudo nvidia-settings --no-config

That did not change anything...

---

### Post by dinxter on 2009-09-23
how about, when you click on 'save to x configuration file' specify another place such as your desktop and copy it across to /etc/X11

---

### Post by froggyswamp on 2009-09-23
If I got you right, try this:
By default xorg.conf is empty or not "compatible" with the nvidia proprietary "nvidia-settings" driver/app (whatever it's called), hence before using 'nvidia-settings', first create a "compatible" xorg.conf file by issuing "sudo nvidia-xconfig" (from terminal) which will do just that. Then as usually run nvidia-settings (as root so that it can' save to /etc/X11).

---

### Post by gjoellee on 2009-09-23
> **dinxter said:**
> how about, when you click on 'save to x configuration file' specify another place such as your desktop and copy it across to /etc/X11

I don't know how that is possible, I don't think it is possible without modifying code for the Nvidia program.

> **froggyswamp said:**
> If I got you right, try this:
By default xorg.conf is empty or not "compatible" with the nvidia proprietary "nvidia-settings" driver/app (whatever it's called), hence before using 'nvidia-settings', first create a "compatible" xorg.conf file by issuing "sudo nvidia-xconfig" (from terminal) which will do just that. Then as usually run nvidia-settings (as root so that it can' save to /etc/X11).

Tried, but did not work...

---

### Post by gjoellee on 2009-09-23
Open Nvidia settings from terminal. Take a look a this output maybe?
```
$ nvidia-settings

(nvidia-settings:1988): Gtk-WARNING **: Invalid size in gtk-icon-sizes: 0,0


VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".

Segmentation fault (core dumped)
```

---

### Post by dinxter on 2009-09-23
> **gjoellee said:**
> I don't know how that is possible, I don't think it is possible without modifying code for the Nvidia program.
the version of nvidia-settings in karmic gives you a pop up box when you click the button, you can choose the file to save to, i did it before posting to test it works, and it did!

---

### Post by gjoellee on 2009-09-23
> **dinxter said:**
> the version of nvidia-settings in karmic gives you a pop up box when you click the button, you can choose the file to save to, i did it before posting to test it works, and it did!

I am not getting that button. Just a new little error window.

---

### Post by dinxter on 2009-09-23
> **gjoellee said:**
> I am not getting that button. Just a new little error window.
ah, why not just mv /etc/X11/xorg.conf out of the way somewhere and then use nvidia-settings, since your going to generate a new one anyway

---

### Post by gjoellee on 2009-09-23
> **dinxter said:**
> ah, why not just mv /etc/X11/xorg.conf out of the way somewhere and then use nvidia-settings, since your going to generate a new one anyway

Done that already :P

---

### Post by dinxter on 2009-09-23
> **gjoellee said:**
> Done that already :P
i dont understand, you get,
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".
when /etc/X11/xorg.conf doesnt exist!

---

### Post by gjoellee on 2009-09-23
> **dinxter said:**
> i dont understand, you get,
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".
when /etc/X11/xorg.conf doesnt exist!

Oh, you mean doing it that way...I moved the xorg.conf and made a new one with nvidia-xconfig.

Uhm, tried it now. It works they way that I can copy and paste now. That works enough for me.

Thanks :p

---


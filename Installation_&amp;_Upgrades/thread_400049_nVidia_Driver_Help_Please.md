---
title: "nVidia Driver Help Please?"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by groovdafied on 2007-04-03
Hi Everyone,

I recently installed ubuntu a last week, and I'm very new to this. I've tried searching this forum, but I'm unable to locate the answer to this problem.

So I followed the instructions to install nVidia drivers from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) and it works great when I went through the steps.

However when I reboot or shut-down and turn back on my PC, it says it cannot locate the nVidia kernel or something. In general, it displays an error message in command line and wont load the GUI unless I boot up in safe mode and type;

sudo rmmod nvidia && sudo modpprobe nvidia

&

sudo /etc/init.d/gdm start (to load the gui back on)

What am I doing wrong?:confused:

---

### Post by 1/0 on 2007-04-03
I guess the nvidia module is not loaded correct. If *ubuntu works somewhat the same way as Gentoo you could load it automatically at boot by adding nvidia in the modules file.

```

sudo nano -w /etc/modules

```

That might do the trick.

---

### Post by groovdafied on 2007-04-03
> **1/0 said:**
> I guess the nvidia module is not loaded correct. If *ubuntu works somewhat the same way as Gentoo you could load it automatically at boot by adding nvidia in the modules file.

```

sudo nano -w /etc/modules

```

That might do the trick.

Um...ok...I really don't know what to do, it looks like I can modify something, should I enter in the commands to reload the nvidia?

---

### Post by 1/0 on 2007-04-03
With that command you use nano as editor ("man nano" for help). Enter nvidia on a separate line at the bottom. Then to save and exit press ctrl + x and press Y for yes. (All the commands at the bottom are meant to be used with ctrl and the letter.)

I hope that helps. Otherwise you could use any other editor you'd like, as long as you're doing it as root/sudo.

---

### Post by 1/0 on 2007-04-04
Did it work out for you?

---

### Post by groovdafied on 2007-04-04
> **1/0 said:**
> Did it work out for you?

I'm gonna try tonight....as for the error, I managed to remember it. It starts up in the command line only showing X11 unable to start up.

---

### Post by BlowHole13 on 2007-04-08
Ok, so I just spent the last few days resolving this exact problem. The installation directions for the nVidia driver @ the beryl-project are wrong! I had the same problem, my system would boot to a terminal because X11 would not start. the kdm would, but not X11. The only way to get it going, was to reinstall the drivers again, but when I would reboot... same problem. The correct way to install the nVidia driver I found here [http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412) and now everything works perfectly! if you were installing the way beryl-project says to, you might have gotten some of the same errors as I (forced to guess the x library path 'usr/lib' and x module path /usr/lib/xorg/modules', etc, ect) even though the driver would work fresh off an install. when installed with the new way here THERE WERE NONE OF THESE WARNINGS WHATSOEVER! now everything works like a charm! including beryl (beryl is sooooooo very cool!) hope this works things out for you. It sure did for me!

---


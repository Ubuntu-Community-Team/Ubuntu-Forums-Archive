---
title: "Able to get desktop in Jaunty on i845G"
date: 2008-12-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-29
Hi all, 
 I was able to get a usable desktop but had to do some running around.  This is with the latest kernel 2.6.28-4.4

This is what I did. 

1. Go to recovery mode. 
2. Made changes in /etc/X11/xorg.conf using nano (feel free to use your own x editor)

In Section "Device" made the following changes. 

 ```
Section "Device"
             Identifier "Configured Video Driver"
             Driver      "Intel"
             Option      "NoAccel""true"
             Option      "ModeDebug""true"
             Option      "FallbackDebug""true"
 EndSection
```

then started dbus and then hal as both seem to be not working at root prompt.  

```
/etc/init.d/dbus status 
```

start dbus 

```
/etc/init.d/dbus start
```

same for hal 

```
/etc/init.d/hal status
```

start hal 

```
/etc/init.d/hal start
```

then changed user to my username from root

```
su shirish
```

then did startx 

```
$startx
```

it worked. 

.xsession-errors has some errors and haven't seen /var/log/Xorg.0.log as well. 

The only thing is it paints the screen when you use the cursor to go either up or down, noticeable but still usable.

---

### Post by vishalrao on 2008-12-29
i think dbus/hal were not started because recovery root shell is in single user mode. doing "telinit 5" goes to multiuser console runlevel 5, or so i believe. thats what i figured when installing nvidia 180.18 today :D

---

### Post by jerrylamos on 2008-12-30
Thanks, ShirishAg75!  jaunty upgrade and CD Live were dead in the water!

In my IBM NetVista A30 with i845G, similar to what you did, from root shell prompt
vim /etc/X11/xorg.conf

Section "Device"
       Identifier     "Configured Video Device"
       Driver         "Intel"
       Option         "NoAccel"    "true"
EndSection

did the trick.  
Also, after saving the change, do 
exit
resume normal boot

which seems to take care of the other things that aren't started yet.

Note, on CD Live which has the same problem, edit the boot line 
remove:  quiet splash
add:     single
which gives CD Live the recovery mode, then edit xorg.conf as above.

Thanks much!

Jerry

---

### Post by jerrylamos on 2009-01-01
The preceding workaround also worked on my IBM Thinkpad R31 which has Intel 82830 graphics.

Scroll is a bit slow.  Flashplayer works fine for that speed processor.

Jerry

---

### Post by DougieFresh4U on 2009-01-05
I want to say thanks as this thread helped me. Last week I had the thread where my desktop was locking up/freeze so I ask for help and put it back to the 'vesa' driver. so I was wondering this week if any changes to the 'Intel' driver(I have the 865G chip) and I cahnged from 'vesa'. Upon reboot I was met with the ole freeze/lock up drama. So I had remembered reading this thread and I went in via live cd and edited 'x' using info from this thread. Rebooted and all seems stable, flash working, etc.. Only problem I see is scrolling through browsers is slow and a bit 'choppy', but hey thats better than freeze/locked up desktop and having to do hard shut downs. 
Thanks to all who supplied info in this thread.
They still need to work on that 'Intel' issue

---

### Post by maheshasolkar on 2009-01-14
Isn't there a way to use an old version of xserver-xorg-video-intel until the new version is usable with acceleration?

---

### Post by darkenergy on 2009-01-14
> **maheshasolkar said:**
> Isn't there a way to use an old version of xserver-xorg-video-intel until the new version is usable with acceleration?

I'd also highly appreciate that...



my xorg.conf after reinstalling jaunty is completely empty - maybe there is a problem somewhere in the config script that should write the xorg.conf?

---

### Post by maheshasolkar on 2009-01-14
> **darkenergy said:**
> my xorg.conf after reinstalling jaunty is completely empty - maybe there is a problem somewhere in the config script that should write the xorg.conf?

I won't be surprised if the empty xorg.conf is intentional. That appears to be the general direction things are moving - defaults work in most case. If you need to tweak options for performance/fine tuning or to get something working (the NoAccel option in this case).

There is a *Package -> Force Version* option in Synaptic. I was wondering if that could be used to roll back the video-intel package a version. But that option is greyed out.

---


---
title: "Lucid on MacBooks"
date: 2009-11-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2009-11-23
[We had a similar thread about this for the Karmic release.]("http://ubuntuforums.org/showthread.php?t=1245957")
Please post how Lucid works on your Mac.

In this early development, everything seems to work on my MacBook (5,1). 
However, the laptop getting really hot and the battery life isn't that good compared to OS X. I might have 1.5 hour normal use.

---

### Post by hanzomon4 on 2009-11-23
You might want to file a bug on the battery life issue. Battery life has always be atrocious on macs, probably all laptops, it's about time it gets addressed. I would file a bug but I running karmic still and can't risk an upgrade

---

### Post by Gina on 2009-11-23
I've noticed extra CPU load with Karmic and Lucid as I posted in [the overheating thread]("http://ubuntuforums.org/showthread.php?t=1334671").

---

### Post by davideotape on 2009-11-23
I'm on a MacBook 5,2.

[LIST]
[*]My sound doesn't work ([https://bugs.launchpad.net/bugs/463178](https://bugs.launchpad.net/bugs/463178))
[*]Overheating is a problem. ```
sudo echo 3250 > /sys/devices/platform/applesmc.768/fan1_min
``` solves it temporarily. ([http://bugzilla.kernel.org/show_bug.cgi?id=14514](http://bugzilla.kernel.org/show_bug.cgi?id=14514) and [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/461184](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/461184))
[*]My touchpad is nowhere near sensitive enough. ([https://bugs.launchpad.net/bugs/416516](https://bugs.launchpad.net/bugs/416516))
[*]I can't reboot from Ubuntu back into Ubuntu (all other combinations seem to work fine)
[/LIST]

And that's about it for me.

---

### Post by davideotape on 2009-11-25
Oh, and the black and white circle of friends is stretched on boot for me too.

---

### Post by Tompalaz on 2009-12-12
Alright, things might have developed now that alpha1 is here..

I've got this interesting problem: [http://ubuntuforums.org/showthread.php?t=1350632](http://ubuntuforums.org/showthread.php?t=1350632) 

The new Xorg detects the acceleration sensors as a joystick. My mouse keeps jumping back to the center of the screen, which is kind of annoying.

---


---
title: "New Xorg, new Joystick?"
date: 2009-12-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Hiram on 2009-12-09
I just updated to the new Xorg and noticed that my mouse keeps skipping back to the center of the screen. 

After some research i found that this happens a lot when you have a joystick connected. But I don't have a joystick on my macbook... Or so i thought... 

Appearantly the new Xorg detects the acceleration sensors in my macbook as a joystick and although that is nice if i want to play neverball, it isnt so much in everyday use.

Does someone know where i can find settings to configure my 'joystick?'

Edit: Ah rmmodding applesmc resolves the problem, but i recall that it was loaded on boot before.
I also suspect that other less experienced users can encounter the same problem and stop using ubuntu.

Does the hd protection (thats where the sensors are for) still work?

---

### Post by Tompalaz on 2009-12-12
> **Hiram said:**
> 

Edit: Ah rmmodding applesmc resolves the problem, but i recall that it was loaded on boot before.
I also suspect that other less experienced users can encounter the same problem and stop using ubuntu.

Does the hd protection (thats where the sensors are for) still work?

I got this problem too, how do I rmmodding applemc?
edit: is it rmmod <packetname>? because I don't have applesmc installed and cant install it either

---

### Post by VMC on 2009-12-12
> **Hiram said:**
> I just updated to the new Xorg and noticed that my mouse keeps skipping back to the center of the screen....

I noticed this too yesterday. I only using a mouse on a PC. Thought  it had something to do with my mouse. Didn't relate it to Xorg, now that you mentioned it.

Today though, I no longer have that problem. There has been some updates. Maybe it got fixed. For me at least.

---

### Post by Tompalaz on 2009-12-13
I don't get rid of this problem and I can't install the applemc package either (so I could rmmod it)

VMC, did you upgrade the xserver packages that have been held back or do you have another PPA for xserver?

---

### Post by sroecker on 2009-12-13
Tompalaz, just do
```
rmmod applesmc
```You don't need to install anything, applesmc.ko is in linux-kernel-generic.

The problem is  I need applesmc because it provides sensor (fan, temperature etc) data.
Is there another way to disable this "joystick"?
Btw, 2-click-rightclick also doesn't work anymore.

---

### Post by Tompalaz on 2009-12-13
Thank you!!!!
That did the trick!

---

### Post by hugmenot on 2009-12-13
> **sroecker said:**
> Tompalaz, just do
```
rmmod applesmc
```You don't need to install anything, applesmc.ko is in linux-kernel-generic.

The problem is  I need applesmc because it provides sensor (fan, temperature etc) data.
Is there another way to disable this "joystick"?
Btw, 2-click-rightclick also doesn't work anymore.

Perhaps applesmc has module load options. You can check with »modinfo applesmc«.

---

### Post by tepsipakki on 2009-12-13
The evdev udev rules are wrong, it shouldn't load for devices that have accelerometers. It'll get fixed before too long, so no need to keep using those blacklists after the fix is in.

---

### Post by sroecker on 2010-01-06
Until it's fixed you can do this as a workaround (not permament though):

```

xinput list # to get the id of applesmc
xinput float id

```Now it doesn't move the core pointer anymore.

---


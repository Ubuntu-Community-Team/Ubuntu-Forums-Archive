---
title: "Mighty mouse stopped working after upgrade to Hardy"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by peter.marks on 2008-05-06
I've been using an Apple Mighty Mouse on be Feisty setup absolutely perfectly with the setup:

```
Section "InputDevice"
    Identifier "MightyMouse"
    Option "CorePointer"
    Driver "evdev"
    Option "Name" "Primax Electronics Apple Optical USB Mouse"
    Option "HWHEELRelativeAxisButtons" "7 6"
    Option "Buttons" "8"
EndSection
```

After upgrading to Hardy, it just stopped working. No cursor movement, nothing. I can get a usable config switching back to a generic mouse:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

but obviously I don't get the Mighty Mouse features.

Also, just noticed that that config mentions ImPS/2 which is odd because this is a USB mouse.

Any suggestions?


Peter

---

### Post by Ezzizzle on 2008-05-07
I've had at least a similar problem to yourself.

After the upgrade from Gutsy to Hardy I had a few headaches getting my nVidia drivers re-set up and my Apple keyboard to work correctly but through following guides on the Ubuntu forums and other sites I was able to get everything working as it should be except for my Mighty Mouse.

I had the Mighty Mouse working fine in Gutsy with this config:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
	Option "CorePointer"
	Driver "evdev"
	Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
	Option "HWHEELRelativeAxisButtons" "7 6"
	Option "Buttons" "8"
EndSection
```

When I first upgraded I had no cursor movement either so I reverted to this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "HWHEELRelativeAxisButtons" "7 6"
    Option         "Buttons" "8"
EndSection
```

Which gives me everything except for Horizontal Scrolling which I'd really like to get back.

---

### Post by peter.marks on 2008-05-08
Thanks Ezzizzle

I guess your config is slightly better than mine as it should allow me to assign functions to other buttons, but the only feature I want beyond what I have is the horizontal scroll. Shame about that.

Looks like you have a similar set up to me. How did you get your keyboard sorted? I have the same one and have all the problems described in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887). I just want it to behave like it did in Gusty with all the keys back where I expect them to be. I don't care about the media keys.

I got my nVidia card sorted and got Emerald to be my default window manager again, but I can't get rid of some flickering I now get when mousing over title bars.


Peter

---


---
title: "Logitech MX Revolution and Jaunty (9.04)"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by t.rei on 2009-04-03
Hi,

I was wondering if anyone else has the same thing happeing:

My MX Revolution's buttons >5 (1,3,wheelclick, mwheelup, mwheeldown) do not register as existant in X.

I can assign them to toggle the wheel behaviour using 'revoco'.

I cannot - not with any driver and any howto and any protocol get those additional buttons to work in X. I tried the lot. 'xev' wont even recognize them as being pressed.

currently I am using:
```

Section "InputDevice"
        Identifier      "MX"
        Driver          "evdev"
        Option          "Device"        "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
EndSection
```and 
```
sudo revoco click
``` to get my mousewheel click to be my middle-mouse-button.

This is my mouse:
```
ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
```I'd love to see my browser-buttons working again. And maybe even the thumbwheel.

Anyone having those issues? If you have something working, please post.

---

### Post by t.rei on 2009-04-04
Ok, I have tested alot this day and found several hints pointing towards the current state of evdev/hal/xinput ... being utter rubbish.

I cannot complain about it being in jaunty - BUT I can complain if it this is the state considered releasable. O_o

Does anyone know if it is possible to "force" the logitech receiver to be perceived as a "plain" old "5 button + 1 wheel" mouse? (at least) 

Working is cool.
New is cool.
Going from working to "using something new that isn't" is not cool.

---

### Post by phenest on 2009-04-04
I'm using a Kensington bluetooth mouse. It also has 5 buttons plus a wheel and works perfectly.

Does it work using a Live CD?

---

### Post by t.rei on 2009-04-04
Good point.

And freakyness:
It works with a Intrepid LiveCD
It works with the Jaunty LiveCD
It does not work when upgrading from Intrepid to Jaunty

Now I do have issues reinstalling Ubuntu to get my MOUSE to work, but since I see no other way, I might do that. :/

Unless you do have another pointer at how to get things sorted again.

Also: this might be something the Jaunty Developers should be aware of, if reproducable.

---

### Post by tepsipakki on 2009-04-04
I've used MX Revolution for a year now, and every button works (at least they generate events, too bad GNOME doesn't support setting shortcuts to them). You only need to use revoco once, so what's the problem?

---

### Post by tepsipakki on 2009-04-04
if it works in the livecd, then your configuration is messed up. Try moving /etc/X11/xorg.conf out of the way first.

---

### Post by phenest on 2009-04-04
If you've put anything in the xorg.conf file, remove it. The only thing the xorg.conf file is used for really is video these days.

I'm not sure where mouse settings are stored.

---

### Post by lucazade on 2009-04-04
I've got a MX Revolution and i usually map the middle-button using xmodmap.

xmodmap -e "pointer = 1 8 3 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"

side button will work as the middle one.

---

### Post by t.rei on 2009-04-04
I used the xorg.conf as empty as it was from the jaunty CD - it won't work. 

So now I will do a fresh install on another partition and check it out. At least there is hope now. Thanks guys.

Mapping the Buttons is a whole different story, but I will get to that once they at least generate events. ;)

---

### Post by t.rei on 2009-04-04
Ok, the hint about trying the live-CD got me to do the unthinkable:

reinstall formatting only the system-partition (thats why I keep them seperate! *g*)

While not bein impressed at all with the upgrade screwing me over, the new install went so fiendishly flawless it's almost boring. Also the import-feature of found users (it even offered importing from the windows partition :shock:) made getting back to work really painless.

So. 

To everyone else having problems: xorg.conf looks like this:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
The only thing I added was the "nvidia" after installing the proprietary drivers. *sigh*

I don't know what messed things up. Maybe something hal/evdev related? Some leftover old rules maybe? Well it's working now. *cheers* 

Big thanks go out to the hint about the liveCD - sometimes the obvious solutions elude my eyes.

"Hello IT. Have you tried turning it off and on again?"

---

### Post by phenest on 2009-04-04
> **t.rei said:**
>  Some leftover old rules maybe? 

That would be my guess.

---


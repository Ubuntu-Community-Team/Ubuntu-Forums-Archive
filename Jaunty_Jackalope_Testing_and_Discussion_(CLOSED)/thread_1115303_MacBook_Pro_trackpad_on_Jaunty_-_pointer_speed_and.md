---
title: "MacBook Pro trackpad on Jaunty - pointer speed and click-dragging problems"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skylen on 2009-04-03
I posted this same problem in bug #337935 at [https://bugs.launchpad.net/mactel-support/+bug/337935]("https://bugs.launchpad.net/mactel-support/+bug/337935"), but I am hoping someone here might be able to help me with my pointer speed/sensitivity problem, at least.

I got the trackpad on my MacBook Pro 5,1 *mostly* working by doing:
(On a fresh install of Jaunty Beta)

1. Install all the mactel PPA packages.
2. Blacklist usbhid
3. Put bcm5974, usbhid in modprobe's "modules" file to force bcm5974 to load first.
4. Put the file posted above by P. Dunbar on 2009-03-31 in /etc/hal/fdi/policy

I could then tweak the .fdi file in a minor way and had the following features:

- tap-to-click
- one/two/three-finger tap clicks for left/right/middle button
- two-finger scrolling (both vertical and horizontal)

There are still some big problems that make the trackpad completely unusable for me unfortunately. The main problems are:

1. Sensitivity is *WAY* too low.
2. Can't click and hold with thumb while dragging with another finger.

First, the sensitivity problem. I tweaked the .fdi file's MinSpeed, MaxSpeed, and AccelFactor to achieve much higher speed of movement that is fairly satisfactory -- however, this only has an effect at the GDM login screen! When I actually log in and Gnome starts, the trackpad movement slows down tremendously. Even if I crank up the sensitivity/acceleration in the Preferences|Mouse dialog, it is still too slow. Also, I don't want much "acceleration" I mostly want a constant, moderate sensitivity. This is useful because the MacBook Pro's trackpad is so enormous (which is one of the features that made me choose this laptop).

I cannot use the 'synclient' program, it always says that it can't access the shared memory segment and I should enable SHM support in the synaptics configuration, but it is already enabled in the .fdi file. (Also, there is nothing related to this in the xorg.conf file that could be messing it up.) I tried the 'gpointing-device-settings' program ([http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)) and this provided some easy access to extremely important xinput settings such as palm detection. It did not allow configuring the sensitivity or speed of the trackpad movement.

I would be very happy if the trackpad movement speed at the GDM login screen could simply be preserved when I logged in. Does anyone have an idea how I could do this?

Second, the normal way of dragging things that I use in Mac OS X does not work. I find that double-tap-and-drag is sometimes useful but can be finicky if you don't wait long enough before putting your finger back down after you are done dragging (it will think you still want to drag). I have this problem in Mac OS X too. So I find the most effective way to drag is to use my forefinger to move the pointer and click-and-hold with my thumb on the near edge of the trackpad while I drag with the forefinger. This does not work in Ubuntu; apparently the driver is confused by my thumb's presence on the trackpad surface.

I think that Mac OS X must treat the near (bottom) edge of the trackpad specially when a second finger is detected there, in order to support the particular case where the thumb is used to click in the region on the bottom edge while a finger is moving the pointer elsewhere on the trackpad. I'd be willing to implement this functionality myself if someone could give me a nudge in the right direction; I don't yet understand the relationship between "bcm5974" and "synaptics". Is the trackpad actually a "synaptics" device, or is it a "bcm5974" device but events are being translated and sent to the synaptics X input module as an implementation shortcut instead of making a native bcm5974 X input module?

Thanks for any help; I really want to get Ubuntu working well on my new MacBook Pro and a well-functioning trackpad is a critical component to make the system usable.

---

### Post by droazen on 2009-04-04
Regarding your second issue, have you tried setting the LockedDrags option to "on"? With locked drags, you double-tap once to select (*without* needing to hold the second tap down) -- then you are free to drag the item around at leisure, and it will stay selected even if you take your fingers off the touchpad completely. When you have the item where you want it to be, you single-tap to release.

---

### Post by droazen on 2009-04-04
To clarify, the LockedDrags option is set in your fdi file via a line like the following:

```
<merge key="input.x11_options.LockedDrags" type="string">on</merge>
```

---

### Post by skylen on 2009-04-04
> **droazen said:**
> Regarding your second issue, have you tried setting the LockedDrags option to "on"? With locked drags, you double-tap once to select (*without* needing to hold the second tap down) -- then you are free to drag the item around at leisure, and it will stay selected even if you take your fingers off the touchpad completely. When you have the item where you want it to be, you single-tap to release.

I haven't tried that.  I might try it, and I'll see if it's a better interim solution than the tap-tap-drag.  I think that thumb-press+finger-drag is the best solution though for most of my purposes.

Thanks for the suggestion though; locked drags might be helpful in many cases.

---

### Post by Nikos.Alexandris on 2009-04-11
> **skylen said:**
> I haven't tried that.  I might try it, and I'll see if it's a better interim solution than the tap-tap-drag.  I think that thumb-press+finger-drag is the best solution though for most of my purposes.

Thanks for the suggestion though; locked drags might be helpful in many cases.

I've installed Jaunty on MPB5,1 by cross-comparing with the content of the _new_ wikipage [1]. First the _bad news_:

:( The backlit keyboard function keys do not work (as expected!?)

:( All seems to work like the page describes except of the touchpad. I tried playing around with the .fdi file but no luck to get "tapping" to work.

:p The performance is *much* better than with Intrepid. Fast booting and shutting down.

:p The display brightness keys work (after adding mactel suport packages) 

:p All of the sensors seem to _report_ just fine with (after adding the *coretemp*, *applesmc* modules in **/etc/modules**)  the command ```
sensors
``` I get something like```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +60.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +100.0°C, crit = +100.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :3207 RPM  (min = 2000 RPM)
Right side :3207 RPM  (min = 2000 RPM)
temp1:       +36.0°C                                    
temp2:       +36.0°C                                    
temp3:       +33.5°C                                    
temp4:       +36.2°C                                    
temp5:       +71.8°C                                    
temp6:       +62.0°C                                    
temp7:       +61.8°C                                    
temp8:       +73.0°C                                    
temp9:       +66.2°C                                    
temp10:      +54.5°C                                    
temp11:      +66.2°C                                    
temp12:      +69.2°C                                    
temp13:      +67.5°C                                    
temp14:      +70.0°C                                    
temp15:      +64.8°C                                    
temp16:      +55.0°C                                    
temp17:      +57.5°C                                    
temp18:      +63.5°C                                    
temp19:      +33.2°C                                    
temp20:      +48.8°C
```


Any chance to get the touchpad working out-of-the-box with the mactel packages before the 28th of April?

Thanks to all for their efforts, Nikos
---

[1] [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty")

---


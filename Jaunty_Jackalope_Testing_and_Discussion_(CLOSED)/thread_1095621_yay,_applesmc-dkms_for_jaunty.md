---
title: "yay, applesmc-dkms for jaunty"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inphektion on 2009-03-13
Noticed this package got updated for jaunty...
Still can't get keyboard backlight working, anyone have any pointers?

---

### Post by inphektion on 2009-03-14
```
[   10.658967] applesmc: Apple MacBook Pro 5 detected:
[   10.658969] applesmc:  - Model with accelerometer
[   10.658970] applesmc:  - Model with light sensors and backlight
[   10.658971] applesmc:  - Model with 20 temperature sensors
[   10.716835] applesmc: device successfully initialized (0xe0, 0x00).
[   10.716836] applesmc: device successfully initialized.
[   10.717880] applesmc: 2 fans found.
[   10.727526] input: applesmc as /devices/platform/applesmc.768/input/input12
[   10.736237] Registered led device: smc::kbd_backlight
[   10.736247] applesmc: driver successfully loaded.

```

its all loaded... can't figure out how to control anything though.
Let me know if someone else figured it out.


edit: i see stuff here.. /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight

I can also cd into a bunch of looping folders
sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/device/leds/smc::kbd_backlight

but can't get keyboard backlight on at all still.

---

### Post by inphektion on 2009-03-14
ok if I echo 255 into the brightness file in
:/sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/

then the keyboard backlight comes on.  
Just trying to get F5/F6 to control this now...

---

### Post by niorg on 2009-03-14
You need to install hal-applesmc from the mactel repository i believe. Currently only the Intrepid version is available, but it will work.

Has anyone got the multitouch trackpad to work in jaunty? Xorg enables mouse emulation and that gives me only basic trackpad functionality. No right/middle click and no scrolling.

---

### Post by inphektion on 2009-03-14
no touchpad yet.  I assume we'll need bcm5974 from mactel ppa compiled for jaunty.

---

### Post by niorg on 2009-03-14
There is a bcm5974 dkms for jaunty in mactel repository. I believe we need usbhid-dkms or hid-dkms (i forgot which one) to be released for jaunty to let the touchpad be recognized properly.

---

### Post by inphektion on 2009-03-14
yep your right, was just added.  Seems to need usbhid-dkms.  So close....

---

### Post by cyberdork33 on 2009-03-15
they are getting worked on guys.

usb-dkms and usbhid-dkms are obsolete in Jaunty. You probably need the gnome-power-manager package.

---

### Post by inphektion on 2009-03-15
Well the bcm5974 package for jaunty is there and if you try installing it it says it depends on usbhid-dkms.  So if its obsolete then the bcm5974 package for jaunty will need to be rebuilt or it will never install.

---

### Post by inphektion on 2009-03-19
and it was rebuilt to remove the dependency!
will try it when i get home:
```
bcm5974-dkms (1.1.3) jaunty; urgency=low

  * Removed dependency on usbhid

 -- Henrik Rydberg <email address hidden>   Thu, 19 Mar 2009 02:07:08 +0100
```

---

### Post by cyberdork33 on 2009-03-19
> **inphektion said:**
> and it was rebuilt to remove the dependency!
will try it when i get home:
```
bcm5974-dkms (1.1.3) jaunty; urgency=low

  * Removed dependency on usbhid

 -- Henrik Rydberg <email address hidden>   Thu, 19 Mar 2009 02:07:08 +0100
```
yep, I emailed Henrik about it personally.

---

### Post by inphektion on 2009-03-20
thanks.  I've been messing with it for about an hour now and can't get any right click, scroll etc to work.  
I've tried multiple .fdi files in /etc/hal/fdi/policy
none seem to be used at all as the touchpad behaves the same regardless which is just basic left click functionality.
I even tried removing the generic .fdi in /usr/share/hal/fdi/policy/20thirdparty/ in case it was overriding the ones in /etc.

No clue here, any pointers?

---

### Post by cyberdork33 on 2009-03-20
> **inphektion said:**
> thanks.  I've been messing with it for about an hour now and can't get any right click, scroll etc to work.  
I've tried multiple .fdi files in /etc/hal/fdi/policy
none seem to be used at all as the touchpad behaves the same regardless which is just basic left click functionality.
I even tried removing the generic .fdi in /usr/share/hal/fdi/policy/20thirdparty/ in case it was overriding the ones in /etc.

No clue here, any pointers?
nope. Sounds like you are in the same boat I am in now with my MBP4,1

right-click works as tapping with 3 fingers (i think). I can't get it to change from that. It maybe a problem with synaptics...

Got a bug here:
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

### Post by hanzomon4 on 2009-03-20
I can get my keyboard and screen backlight working... but I have to unload nvidia_bl, reload nvidia_bl, logout and then back in... thats just for screen backlight, the keyboard is the same process except with mbp_nvidia_bl. They're both in /etc/modules and I 've tried disabling one and leaving the other and taking them both out... It still won't work until I complete the steps mentioned above

---


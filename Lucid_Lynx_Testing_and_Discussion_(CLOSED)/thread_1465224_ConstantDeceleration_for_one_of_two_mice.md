---
title: "ConstantDeceleration for one of two mice"
date: 2010-04-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Edward C on 2010-04-29
Hi,

I have a laptop that I use at home and at work. The mouse at work is fine with the default settings, but to properly use the mouse I have at home it needs a ConstantDeceleration set. Earlier versions of Ubuntu used a HAL .fdi file to configure this option, then came udev rules, and now it seems that the method has changed again for 10.04 and the option must be specified in xorg.conf or an xorg.conf.d file. I'm currently facing two issues:

- Though X acknowledges the configuration option, it has no effect.

- Assuming I can tweak the config to get X to apply the option, I have no idea where to begin to configure it for only one of the two mice I regularly use, as was possible with the HAL and udev methods.

Here's what I've added to my xorg.conf:


Section "InputDevice"
        Identifier      "Microsoft Wireless Mouse 5000"
        Driver          "mouse"
        Option          "ConstantDeceleration"  "200"
        Option          "AutoServerLayout"      "true"
EndSection

Section "ServerFlags"
        Option          "AllowEmptyInput"       "false"
EndSection


and here's some of the Xorg.0.log output:


(II) XINPUT: Adding extended input device "Microsoft Wireless Mouse 5000" (type: MOUSE)
(**) Microsoft Wireless Mouse 5000: (accel) keeping acceleration scheme 1
(**) Microsoft Wireless Mouse 5000: (accel) constant deceleration by 200.0
(**) Microsoft Wireless Mouse 5000: (accel) acceleration profile 0
(**) Microsoft Wireless Mouse 5000: (accel) acceleration factor: 2.000
(**) Microsoft Wireless Mouse 5000: (accel) acceleration threshold: 4


I've tried a range of different values for ConstantDeceleration, from my normal setting of 2 up to the ridiculous 200 shown in my pasted examples. Nothing has made the slightest difference.

Any ideas what's wrong here?

And ideas about whether it's possible to target a single mouse with the xorg.conf approach, or will I need to swap config files twice a day?

Thanks,
Ed.

---


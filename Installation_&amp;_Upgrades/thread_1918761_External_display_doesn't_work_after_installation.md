---
title: "External display doesn't work after installation"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by zuko9 on 2012-02-01
Have just installed Ubuntu on my half-dead laptop, screen and HDD are gone, so decided to install Ubuntu on external HDD with external screen connected. All worked fine, no problems during installation, but after it finished installing can't operate the system. Ubuntu ignores the external display (even with closed laptop's lid). System is on, but can't see anything at all. 

Terminal works in recovery mode. Is there any way to make this work?

Thanks a lot!

EDIT

The external screen works fine on the system run from USB, but after installation screen stopped displaying - "No video available"

---

### Post by BC59 on 2012-02-01
Did you try installing the proprietary drivers for your graphics card?

---

### Post by zuko9 on 2012-02-01
No I haven't thought it should work just fine as it worked during installation and on USB.

How do I install it?

---

### Post by BC59 on 2012-02-01
If there is an option for installing drivers you have to install them through the application Additional Drivers (Jockey).

---

### Post by zuko9 on 2012-02-01
During installation it never asked for any additional drivers. Also I'm unable to do anything as when it launches into X11 the screen disconnects.

Maybe I should try this:
[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

Or is there a way to edit xorg.conf that it'd boot with 2nd screen on and would continue to have it on when Ubuntu starts?

---

### Post by zuko9 on 2012-02-02
Still no luck. Tried connecting to internet through pppoeconf and ifconf wlan0 but doesn't work. 

Any ideas how to make that screen work?

---


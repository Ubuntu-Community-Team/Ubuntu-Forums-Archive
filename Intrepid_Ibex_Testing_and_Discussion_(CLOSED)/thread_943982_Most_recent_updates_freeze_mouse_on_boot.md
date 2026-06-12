---
title: "Most recent updates freeze mouse on boot"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kvk on 2008-10-10
I upgraded to Ibex last week- very pleased with the dist. overall. I downloaded the most recent updates today (Oct. 10), and now it takes several boots in succession to release the mouse. It's functional on the log-in screen, but as soon as the desktop opens it's defunct for a few boots.

---

### Post by mkokotovich on 2008-10-10
I can confirm this... Just upgraded and now my mouse and keyboard don't respond.  Multiple reboots haven't worked for me.

I've tried reconfiguring xorg.conf, but no luck.

/var/log/Xorg.0.log contains many lines of:
(EE) Failed to load module "evdev" (module does not exist, 0)
(EE) No input driver matching 'evdev'
(EE) config/hal: NewInputDeviceRequest failed

Also, on a seemingly unrelated note, when I'm logged into tty1, this message keeps popping up:
ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command

---

### Post by wgrant on 2008-10-10
Install xserver-xorg-input-all; I bet you didn't notice xserver-xorg-input-evdev being removed last night.

---

### Post by kvk on 2008-10-10
You are correct!! I indeed did not notice!!

What's the terminal code for that? I'm still on the learning curve.

Thank you!!

---

### Post by kvk on 2008-10-10
Okay- my bad. It's in the Synaptic, but was already marked as installed. I re-installed it, and I'll reboot and see if it's fixed. Thank you!

---

### Post by mkokotovich on 2008-10-10
Well, as X was trying to tell me, evdev was not installed.  This latest update apparently switched control to evdev, but didn't install it.  Fix:
```

sudo apt-get install xserver-xorg-input-evdev
sudo /etc/init.d/gdm restart

```
Installs evdev, restarts X, and everything is working for me.

edit: I see I was too slow... oops

edit2: So was there a reason *input-evdev was removed last night?  Does *input-all install input-evdev, or is it some alternative solution?

---

### Post by wgrant on 2008-10-10
> **mkokotovich said:**
> Well, as X was trying to tell me, evdev was not installed.  This latest update apparently switched control to evdev, but didn't install it.  Fix:
```

sudo apt-get install xserver-xorg-input-evdev
sudo /etc/init.d/gdm restart

```
Installs evdev, restarts X, and everything is working for me.

edit: I see I was too slow... oops

edit2: So was there a reason *input-evdev was removed last night?  Does *input-all install input-evdev, or is it some alternative solution?

xserver-xorg-input-all depends on -evdev. Due to a transition being uploaded, apt-get would have wanted to remove -evdev and -synaptics for about 3 hours last night - some users obviously didn't bother to check what was going to be removed.

---

### Post by ktp on 2008-10-11
seems like lots of people are doing partial update using update managers and not looking at what is being removed.  It is always good idea to wait a day or two to see if when asked to do partial update in alpha/beta builds.  Or least use apt-get to see what is being done.

---


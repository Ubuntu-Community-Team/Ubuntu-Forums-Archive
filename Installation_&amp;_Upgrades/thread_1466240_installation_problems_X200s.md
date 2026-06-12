---
title: "installation problems X200s"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by prince.buster on 2010-04-30
EDIT: problem solved by booting from an SD card instead of (possibly faulty) USB HDD.

so far have been unable to install ubuntu 10.04 on a lenovo thinkpad X200s ...

steps to reproduce:
1. download AMD64 desktop image (in previous releases i used the 32-bit image)
2. create a USB startup disk as per usual
3. boot from the startup disk. so far so good. now the problems:

4. network-manager not running. i start it manually and it appears in the notification area, but the wlan device is 'not managed'. wireless networking worked out of the box in 9.10

5. ubiquity does not work. clicking the install icon does nothing. running it in a terminal gives:
```
Inhibit all polling failed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

6. random crash notifications pop up (not relating to ubiquity)

7. the system does not shut down, and once logged off will not log back in. i have to resort to holding down the power button

has anyone else had a similar experience? could it be due to my switch to the AMD64 release?

---

### Post by iponeverything on 2010-04-30
> **prince.buster said:**
> so far have been unable to install ubuntu 10.04 on a lenovo thinkpad X200s ...



Thanks for saving me the trouble of trying the 10.04 AMD64 release on my wife's x200s! I was going to give it shot seeing how well everything worked out of the box on 9.10 32 bit.

---

### Post by prince.buster on 2010-05-02
no worries, let me know if the 32bit version works!

---

### Post by EmpIzza on 2010-05-04
Hms, it worked right out of the box for me. The AMD64 version that is.

Just wondering, is the wireless switch on the left side turned off? =P

And have you connected by wired connection and let ubuntu update itself? Guessing you did a fresh install by the steps you took?

---

### Post by prince.buster on 2010-05-04
oh good, that's promising. is it possible that they've updated the iso since my original post?

i didn't install at all, as after booting the live usb ubiquity (the graphical installer) would not start - and a host of other errors put me off the whole thing.

perhaps the problem is due to the live-usb process. could you tell me the steps you took to get ubiquity sucessfully running and installing? if i can just get to that point, everything is sweet.

thanks heaps for your help!

---


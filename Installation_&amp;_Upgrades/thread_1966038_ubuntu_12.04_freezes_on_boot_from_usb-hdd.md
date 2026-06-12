---
title: "ubuntu 12.04 freezes on boot from usb-hdd"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by spcm0012 on 2012-04-26
Created a bootable USB with Ubuntu 12.04, after PC boots from USB, whether I choose to install to a hard drive or do a live boot it freezes at the same point. Attached is an image. Any help on how to get through this is appreciated!

**edit : spelling >_<**

---

### Post by spcm0012 on 2012-04-26
Should add, the usb boots fine on other machines. It appears to always freeze up on the nouveau part of the boot up. 

Selfless bump for help.

---

### Post by ricarribe on 2012-04-28
I'm having the same problem here using a Intel Desktop.

---

### Post by ricarribe on 2012-04-28
See if it works for you: [http://askubuntu.com/questions/126091/live-usb-not-booting](http://askubuntu.com/questions/126091/live-usb-not-booting)

---

### Post by spcm0012 on 2012-04-28
Turns out it was a graphics card issue. adding nomodeset to the boot option being used, and it worked fine. I ran into another issue later on where the installer would freeze. So what Ive done now, Is done a clean install of 11.10 and upgrade from there.

---


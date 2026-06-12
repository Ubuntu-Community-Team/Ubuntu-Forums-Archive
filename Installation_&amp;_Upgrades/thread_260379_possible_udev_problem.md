---
title: "possible udev problem"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by grimpy on 2006-09-18
hi everybody, i currently have a problem with i think udev not sure, it started when i upgrade to kernel 2.6.15.26 udev doesn't create my device example '/dev/null' doesn't exist @ boot, when i manually stop start udev everything works fine anybody got an id how this cane be solved?
i just upgraded to 2.6.15.27 it still doesn't work

---

### Post by Tim Prosser on 2006-10-31
Hmmm.  I've noticed the same thing.  I have a USB sound card (M-Audio Transit) which worked fine in Dapper.  It needs a third-party program called "madfuload" to load firmware into the device before it can be used or recognised, and my UDEV rules are set up to do this.

In Dapper it was detected on boot, and correctly assigned as the default ALSA sound card.

In Edgy, it is not detected on boot, but if I "sudo /etc/init.d/udev restart" then it is detected, and a sound dialog appears allowing me to select it as the sound card.

Not sure what has changed with the udev timings - but there is definitely something different.

---

### Post by ZioLupo on 2006-10-31
Same here.

I have a Plextor ConvertX Tv402U unit that worked perfectly in Dapper.

In Edgy I have the same problems: my unit it doesn't work until I do a:
```
sudo /etc/init.d/udev restart
```

E really cannot understand what is cganged. I know that know there is no more initd but upstart but cannot understand why it doesn't work.

I hope someone can help us!

---

### Post by closey on 2006-11-17
> **Tim Prosser said:**
> Hmmm.  I've noticed the same thing.  I have a USB sound card (M-Audio Transit) which worked fine in Dapper.  It needs a third-party program called "madfuload" to load firmware into the device before it can be used or recognised, and my UDEV rules are set up to do this.

In Dapper it was detected on boot, and correctly assigned as the default ALSA sound card.

In Edgy, it is not detected on boot, but if I "sudo /etc/init.d/udev restart" then it is detected, and a sound dialog appears allowing me to select it as the sound card.

Not sure what has changed with the udev timings - but there is definitely something different.

I have the same problem as you. I upgraded from Dapper to Edgy. I've also tried it in a fresh Edgy and it doesn't seem to work (without doing the udev restart).

---

### Post by livingtm on 2006-11-24
I have a similar issue with edgy and my usb convertx video capture box. When i plug in the USB, i have to fxload the firmware manually before the device will function. It seems like the udev rule never takes effect..

---


---
title: "Problem Installing Ubuntu on Raspberry Pi 4"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by waffen on 2022-08-31
Hello,

I am trying to install Ubuntu 22 on a Raspberry Pi 4 that has a 7" LCD ([https://www.ebay.com/itm/274445786540?var=575053758601](https://www.ebay.com/itm/274445786540?var=575053758601)) connected to the Display port.
When starting the system I see a black screen and I cannot start the wizard to configure Ubuntu for the first time.
With the same hardware Rasbian runs without problems, any suggestions?

---

### Post by QIII on 2022-09-01
How did you prepare your micro sd card?

---

### Post by waffen on 2022-09-01
> **QIII said:**
> How did you prepare your micro sd card?

Using the RP Imager

---

### Post by QIII on 2022-09-01
Sorry about this one, but I have to ask...

You used the ARM port, correct?

---

### Post by waffen on 2022-09-01
I'm using this option: [https://cloud.lacunza.biz/index.php/s/cFE6ZKtjH8tzET8]("https://cloud.lacunza.biz/index.php/s/cFE6ZKtjH8tzET8")

---

### Post by QIII on 2022-09-01
I like to go to the original source for such things.  I figure Canonical knows better than a third party ... and the image is certainly not sullied.

Have a look at [this]("https://ubuntu.com/download/desktop").  I think it would be much easier for everyone to help knowing that you have gone by the "official" method.

---

### Post by waffen on 2022-09-01
OK I'll going to install with that image... I'll write the results here.

---

### Post by waffen on 2022-09-01
I run the new image and after I saw the multicolor screen the blank screen appears again....connected using cable to my router I can see the RPi got IP I can see the lan port working, yellow and green lights are there...

I try SSH but:

>ssh pi@192.168.0.90
ssh: connect to host 192.168.0.90 port 22: Connection refused

What can I do?

---

### Post by waffen on 2022-09-01
I did a workaround: Installed ubuntu server and after that I installed ubuntu-desktop all fine I can launch the Ubuntu gui with no problem. Touchscreen works fine.

Firefox is not installed by default.

BUT now I can't see my home Wifi or the others in the zone  and the Bluetooth don't work, in the settings app both options keep thinking or searching and the list kepp blank...any ideas?

---

### Post by waffen on 2022-09-01
Bluetooth is working now.

---

### Post by waffen on 2022-09-01
I'm closing this thread beacuse I can do a workaround and install the desktop. I'll post another thread for the wifi, thanks!

---


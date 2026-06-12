---
title: "Raspberry Pi 2 does not boot on ubuntu-18.04.4-preinstalled-server-armhf+raspi3.img"
date: 2020-03-19
forum: Installation &amp; Upgrades
---

### Post by jordana2 on 2020-03-19
My good old Raspberry Pi 2 does not boot on ubuntu-18.04.4-preinstalled-server-armhf+raspi3.img but keep blinking its green LED 7 times in a cycle which means there is no kernel.img on first fat32 partition as expected. After dd this img I see indeed no kernel.img on first fat32 system-boot partition:
pi@raspberrypi:/media/pi/system-boot $ ls -la *.img
-rw-r--r-- 1 pi pi 20269704 Feb  3 18:32 initrd.img
pi@raspberrypi:/media/pi/system-boot $

Does this mean that I can not install ubuntu on my good old Raspberry Pi please?

---

### Post by jordana2 on 2020-03-20
Realised I have a Raspberry Pi 1 so out of luck here.

---

### Post by him610 on 2020-03-20
You might want to reconsider installing Raspbian (it's based on stretch now) - it was tailored specifically for the Rpi family from the beginning.

---

### Post by jordana2 on 2020-03-22
Thank you - I moved back to Raspbian indeed. It is based on buster now actually :)

---


---
title: "nvidia and dual screens"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2009-10-18
Usng the latest nvidia drivers. If i run nvidia-settings as root then try to setup daul screens each as a sperate x session when i click on write xconfig file it fails. Is there a different way to enbale dual screens?
Running the latest nvidia drivers and 32 bit karmic with all updates applied

---

### Post by WiFi Ed on 2009-10-18
> **lime4x4 said:**
> Usng the latest nvidia drivers. If i run nvidia-settings as root then try to setup daul screens each as a sperate x session when i click on write xconfig file it fails. Is there a different way to enbale dual screens?
Running the latest nvidia drivers and 32 bit karmic with all updates applied

This is what I do to setup twinview. I don't know if this will work for separate x sessions though.


First run: "sudo nvidia-xconfig"   That seems to sort out xorg.conf.

Second, run: "sudo nvidia-settings"

---


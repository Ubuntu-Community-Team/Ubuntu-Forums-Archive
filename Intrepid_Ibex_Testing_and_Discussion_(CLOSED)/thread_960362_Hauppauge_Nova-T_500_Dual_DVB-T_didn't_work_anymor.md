---
title: "Hauppauge Nova-T 500 Dual DVB-T didn't work anymore"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Archmage on 2008-10-27
```
Oct 27 16:22:23 Test810 kernel: [   18.312336] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
Oct 27 16:22:23 Test810 kernel: [   18.312344] firmware: requesting dvb-usb-dib0700-1.10.fw
Oct 27 16:22:23 Test810 kernel: [   19.199488] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
Oct 27 16:22:23 Test810 kernel: [   20.356072] dib0700: firmware download failed at 26194 with -110
```

Is was working flawless in 8.10 Beta, but after upgrading to the latest upgrades it didn't load the firmware any more.

Can someone please help me?

---

### Post by Teamgeist on 2008-10-27
Is the package linux-firmware installed?

---

### Post by Archmage on 2008-10-27
> **Teamgeist said:**
> Is the package linux-firmware installed?

Yes, it is.

```
aptitude search linux-firmware
i   linux-firmware                                                 - Firmware for Linux kernel drivers                                       
```

If you need more information, this is a AMD64 with the 64bit-version Ubuntu installed. Please tell me if you need more information.

---

### Post by Archmage on 2008-10-28
I'm sorry, but did someone have a clue what I can do about this?

It used to work in the Beta-Version, but now it dosn't work.

Is it possible to get a verbosed information what did went wrong? "dib0700: firmware download failed at 26194 with -110" isn't telling WHY it failed.

---


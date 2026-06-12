---
title: "Lenovo Ideapad installation: wifi dongle not recognized"
date: 2018-05-17
forum: Installation &amp; Upgrades
---

### Post by jrwoodward on 2018-05-17
[COLOR=#454545][FONT=&quot]I am installing **Ubuntu Server 18.04** to a **Lenovo Ideapad 1208-11iAP** (Model 81A4) with 2 gig of memory and a 64g hard drive. The installation medium is a usb thumb drive. I am using an **Iogear Model#GWU627** wifi usb dongle, which has previously worked with two other computers.

[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot]The installation runs correctly until **Step 4/9**, "*Configure at least one interface this server can use to talk to other machines, and which preferably provides sufficient access for updates.*"[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot]There is **no network interface to configure**; no list and just plan space on the screen. If I select "Done" anyway, I get the error message "*Network configuration times out; please verify your settings.*"[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot]I have read about using dongles for network access so that Linux installations can be completed and the wifi set up. But I have not been able to find an instance when the dongle wasn't recognized and offered up for configuration. The Iogear dongle has a steady green power light and a blinking green WLAN light. I can ping it at static address **192.168.1.252**, so I conclude that it is working and properly configured. Removing and reconnecting the usb dongle does nothing. When I switch the dongle and the usb thumb drive, the installation works (up to step 4), so it isn't a bad usb port.

[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot]How do  I get the Ideapad to recognize the dongle?[/FONT][/COLOR]

---

### Post by jrwoodward on 2018-05-18
OK, after being advised that Ubuntu Server will not run well on 2 gig of memory, I switched to installing Desktop. An acquaintance advised me that I could run the LAMP stack on Desktop just fine for development purposes. Desktop installed perfectly; the dongle worked and the drivers for the native wifi card installed as updates. I still wonder why the usb wifi dingle wasn't recognized by the Server install, though. Problem solved!

---

### Post by jeremy31 on 2018-05-18
Could you post results from terminal for ```
lsusb
```
I don't remember model numbers very well

---


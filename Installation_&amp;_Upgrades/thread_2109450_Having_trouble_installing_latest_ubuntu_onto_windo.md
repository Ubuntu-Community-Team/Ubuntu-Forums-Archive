---
title: "Having trouble installing latest ubuntu onto windows8"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by Tom6153 on 2013-01-27
I just brought an advent laptop with windows 8, i put ubuntu onto my pendrive using the linux pendrive installer program recomended on the ubuntu website but when i rebooted the computer it didn't give me the option of booting from the pendrive,
next i went to advanced start up options and clicked the option to reboot from the pendrive and it recognised the pendrive was there but still no ubuntu
so now i am a little stuck
what can i do?
will apreciate the help

---

### Post by Tom6153 on 2013-01-27
i even tried going to the uefi part of the special startup options and i changed the boot order so that windows was disabled and the pendrive was number one but it still booted up windows

---

### Post by darkod on 2013-01-27
Hold on, lately there are many changes with the new UEFI boot type and also Secure Boot. Win8 preinstalled machines usually come with both these days. Read more on that subject before forcing ubuntu to install.

First, go into bios and disable secure boot if you want to install any version older than 12.10. Only 12.10 supports secure boot. Maybe this is why it won't boot the stick.

Second, only the 64bit version is UEFI compatible, so you have to use 64bit.

Third, when booting from the stick, there will be two different boot devices: the UEFI mode of the stick, and the older legacy boot mode. You need to select to boot in UEFI mode so that ubuntu installs in UEFI mode too. Otherwise you won't have uefi dual boot.

Even if you do all of the above, the process is not as simple as before. Thank MS and manufacturers for that. Welcome to the new era, where you don't have control what you install on your own machine. :)

---

### Post by Tom6153 on 2013-01-27
ok thanks, ill change to 64 bit first, 
i just figured out how to switch the secure boot thing off so thats done
not sure i understand the other stuff but lets have a go..

---

### Post by darkod on 2013-01-27
Persoanlly I'm staying away from UEFI, so I don't have first hand experience. Just hwat I have seen here.

Maybe this can help you a bit:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Tom6153 on 2013-01-27
got it installed but now the wireless is not working, is that a side effect !!!!!!!!?????

---

### Post by darkod on 2013-01-28
It shouldn't. Maybe it doesn't have the driver by defauls, or doesn't recognize the card with the exact chipset that it has (it thinks it's another one and loads the wrong driver).

Google for the card model and the ubuntu version installed to see if it turns up anything.

Open another thread in the Networking subforum where there are more people that know much more about the networking drivers.

---


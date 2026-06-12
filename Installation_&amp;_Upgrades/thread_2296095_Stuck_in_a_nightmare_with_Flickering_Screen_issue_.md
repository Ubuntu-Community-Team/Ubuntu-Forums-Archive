---
title: "Stuck in a nightmare with Flickering Screen issue in Ubuntu 12.04.5 LTS after update."
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by nickw2 on 2015-09-23
Hello all,

Wondering if you can help. I am struggling to fix an issue with flickering/blank screen on boot up with Ubuntu 12.04.5 LTS after performing a simple system update from Ubuntu yesterday. I have asked the question on ASKUbuntu but have not been able to resolve with the nomodeset modification within Grub and rebooting the machine. I have tried booting with older kernels but still with no luck. The screen is in blinking mode and then proceeds to blank screen. I can ping the pc and it has an ip address. I cannot load a tty console by using the Ctrl-Alt-F1-6 entries either.

I'm really not sure what to try next but cannot get a console screen up at all as I'm stuck at boot up with no screen.

Any suggestions gratefully received. I cannot really understand how an LTS release can be rendered inoperable by a simple system update..

many thanks,

Nick

---

### Post by QIII on 2015-09-23
Hello!

Can you provide us your machine's hardware specifications?

---

### Post by nickw2 on 2015-09-23
Apologies, forgot to include that at start. I do have nvidia graphics.

My PC is a Dell D620 Latitude Core 2 Duo T7200 2.00Ghz with 4Gb RAM.

Graphics is 256Mb NVIDIA Quadro NVS 110M.

Ubuntu 12.04 amd64 has been installed on this laptop for approx 3 years now and no problems before with system update. From memory I was using the 'recommeded' 304 NVIDIA driver...

Thanks...

---

### Post by nickw2 on 2015-09-23
Hello..
My screen is flickering even when I access the BIOS. Could this be indicative of a hardware problem rather than software?

many thanks,

Nick

---

### Post by v3.xx on 2015-09-23
> **nickw2 said:**
> Hello..
My screen is flickering even when I access the BIOS. Could this be indicative of a hardware problem rather than software?

many thanks,

Nick
What about when plugged into external power?

---

### Post by nickw2 on 2015-09-23
Exactly the same behaviour and also the same when I'm connected to an external monitor via DVI.
It started to go wrong shortly after doing a system update and HP Printer software update....

---

### Post by v3.xx on 2015-09-23
If you have flickering in bios, thats before any OS is loaded.  Does your dell have built in diagnostic?

---

### Post by nickw2 on 2015-09-23
I'm wondering if its a physical problem as it does occur in the BIOS. There are no diagnostics on the machine now. I think there was when it was an MS XP machine but when I installed Ubuntu the utilities went with that.

I've searched online and there is the possibility of it being a loose connector on the motherboard but it does seem very strange that it all happened immediately after I performed a system update. To be 100% accurate though, it did seem to start happening a minute or so after the update finished, so does that suggest that it isn't a software update issue? i.e. if it was a software issue it would have been instantaneous...

---


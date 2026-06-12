---
title: "Installation Help 64-bit 7.10"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by emoruffino on 2008-04-09
i just got my 7.1 cds in the mail today.

I tried live booting the 64-bit version but as many people my screen goes black but pc is chugging along. I left pc alone for around 1/2 hour and nothing.

I also have vista home premium on my master (which i dont want uninstalled or touched) and i have another hardrive a 80GB samsung which i just formatted. (thats for ubuntu)

i cant 'download' anything BIG because im on dialup and it would take too long.

AMD Athlon 64 X2 4600+ 2.4GHz
2GB ram
nvidia 8600GTS 256mb
lightscribe dvd-rw drive

i think thats all i need, sorry, but im very new to linux OS

---

### Post by Pumalite on 2008-04-09
Install with the Alternate Ubuntu CD and configure your xserver at the end of the installation (64 bit). You can download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Check box below sign 'Start Download'

---

### Post by emoruffino on 2008-04-09
> **Pumalite said:**
> Install with the Alternate Ubuntu CD and configure your xserver at the end of the installation (64 bit). You can download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Check box below sign 'Start Download'

this would take too long on dialup is this the only option?

---

### Post by overdrank on 2008-04-09
> **emoruffino said:**
> i just got my 7.1 cds in the mail today.

I tried live booting the 64-bit version but as many people my screen goes black but pc is chugging along. I left pc alone for around 1/2 hour and nothing.

I also have vista home premium on my master (which i dont want uninstalled or touched) and i have another hardrive a 80GB samsung which i just formatted. (thats for ubuntu)

i cant 'download' anything BIG because im on dialup and it would take too long.

AMD Athlon 64 X2 4600+ 2.4GHz
2GB ram
nvidia 8600GTS 256mb
lightscribe dvd-rw drive

i think thats all i need, sorry, but im very new to linux OS

Hi and in addition to Pumalite
You can try and when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 and or 775 then hit enter. Hope this helps. Good luck!

---

### Post by Pumalite on 2008-04-09
You can try vga=791 too.

---

### Post by emoruffino on 2008-04-09
ill try that 

thanks!

---

### Post by sharpycore on 2008-04-09
If neither of these works, I find that in the line that ends "ro quiet splash" just removing "quiet splash" does fine for me.

---

### Post by emoruffino on 2008-04-09
> **sharpycore said:**
> If neither of these works, I find that in the line that ends "ro quiet splash" just removing "quiet splash" does fine for me.

which worked! thanks guys.

no i need to configure my modem and my high definition audio output... :p

---


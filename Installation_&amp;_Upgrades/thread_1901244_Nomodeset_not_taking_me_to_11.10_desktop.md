---
title: "Nomodeset not taking me to 11.10 desktop"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by razaz03 on 2011-12-28
I'm trying to boot into a macbookpro (4,1) using the liveCD to install gdisk and solve my multi-boot MBR issues.

Using gdisk was tedious via OSX (only working OS right now) and as yet my ubuntu partition is useless space.

I can't "try ubuntu before installing" with the liveCD as it takes me to a black screen on my mac, nomodeset seems to load the drivers but it's welcoming me to Ubuntu 11.10 via command line - it won't boot into a graphical environment and I'm not sure why.

The final line displayed is Welcome to Ubuntu 11.10 (Linux 3.0.0-12-generic x86_64) with a 
ubuntu@ubuntu:~$ cursor, and the liveCD boots into a GUI fine in another PC.

Please help!

---

### Post by 2F4U on 2011-12-28
Did you try the failsafe boot option? Also, what are your hardware specs?

---

### Post by razaz03 on 2011-12-28
> **2F4U said:**
> Did you try the failsafe boot option? Also, what are your hardware specs?

failsafe boot option for liveCD? Please ignore my ubuntu installation for now as only gdisk can fix that.

Only tried acpi= and nomodeset boot options from liveCD, don't know how to force failsafe graphics there, please help me with the commands you think are required.

Specs are a 4th gen MacBookPro, googling shows it a 2.6GHz core 2 Duo with 4 GB DDR2 SDRAM memory and a GeForce 8600M GT 512MB graphics card.


Advice required and thanks in advance

EDIT: I have since tried the boot option combinations: "nomodeset acpi=off" replacing quiet splash and after loading drivers etc ubuntu took me to command-line ending in:

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash) 

(initramfs) unable to find a medium containing a live file system.

Once again the usb flash works perfectly in another PC, perhaps it's unable to boot up due to my already existing boot issues? I don't see why that would be an issue as don't liveCDs load their file systems into RAM without relying on other partitions?

---

### Post by razaz03 on 2011-12-28
Sorry for the bump but I'm in need of this laptop!

---

### Post by razaz03 on 2011-12-28
Nobody knows why my liveCD won't boot to desktop instead of command-line?

Please ol' chaps, I beg of thee

---

### Post by razaz03 on 2012-01-03
Still have no clue re this. 

ANY SUGGESTIONS WELCOME.

Thanks

---

### Post by razaz03 on 2012-01-03
So nobody can tell me why I can't boot into ubuntu via the liveUSB?

Can I enlist for any help personally from someone who knows linux well here? Didn't think this issue would take as long as it has

---


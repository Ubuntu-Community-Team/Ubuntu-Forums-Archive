---
title: "Problem While Trying To Install Ubuntu 5.10"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by defubar on 2005-11-24
I just burned the ISO to a dvd and set my BIOS to boot from it and when after I press enter to start the install when it gets to this part:

> devfs:  boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...


It locks up and I have to reboot. I am still rather new to linux in general. Do I need to use some special options? I looked through them but to no avail couldn't get the install going. Any help will be appreciated.

Maybe my hardware will help:

Asus P4P800 Deluxe
P4 2.6 ghz
120gb Seagate SATA-150 HDD
ATI X800 Pro AGP
Intel 538EP Modem
Soundblaster Audigy Platinum

---

### Post by yesplease on 2005-11-24
[http://ubuntuforums.org/showthread.php?t=75155&page=2&highlight=Asus+P4P800+Deluxe](http://ubuntuforums.org/showthread.php?t=75155&page=2&highlight=Asus+P4P800+Deluxe)
has some pointers about flashing the bios and bad CDs.

You can verify your install CD
[http://www.ubuntuforums.org/showthread.php?t=92010&highlight=md5+checksum](http://www.ubuntuforums.org/showthread.php?t=92010&highlight=md5+checksum)

---

### Post by defubar on 2005-11-24
I used the flag "pci=noacpi" and everything worked just fine.  Thanks for the response anyways.

---


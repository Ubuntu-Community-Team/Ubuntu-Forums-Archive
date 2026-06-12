---
title: "Lucid on MBP 5.1"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Aybara on 2010-04-14
Anyone tried it and have something to report? Will the guide for Karmic on 5.1 still give good results?

---

### Post by Niels den Otter on 2010-04-15
Lucid works fine for me on my 5.1. Out-of-the-box installation is much better than previous Ubuntu versions. I would install and see what you miss and fix that if needed. 


-- Niels

---

### Post by Aybara on 2010-04-15
Thanks for the reply. I tried installing from the Beta 2 cd yesterday, but it wouldn't boot. Unsure if it was an error with the CD-R or a bug.

Did you upgrade via apt, or install from cd/dvd?

---

### Post by miatawnt2b on 2010-04-15
The failure to boot LiveCD is a known bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546393)

it works using "nouveau.noaccel=1 blacklist=vga16fb"

-J

---

### Post by Taoye on 2010-04-17
Not sure how relevant it is but I've installed lucid beta 2 on my MBP 5.5 and everything's gone smoothly so far, I followed the guide without problems.

---

### Post by Aybara on 2010-04-17
I tried installing Karmic and upgrading to Lucid via apt-get, but that broke Grub. It said it couldn't install to /dev/sda3. I think this is a known issue, but couldn't find the solution in 5 minutes, so now I'm back in Karmic :)

---

### Post by Aybara on 2010-04-26
Back in Lucid, and everything but wireless is working fine.

Wireless worked fine the first time I connected to my WPA2 network, but not anymore. It sees my network and detects the right security, but it never manages to connect. The network applet just blinks and blinks. I have an open network in my building, but I can't connect to that one either.

---


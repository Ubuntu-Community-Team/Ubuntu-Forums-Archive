---
title: "Wubi Install Boots To GRUB"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2010-03-01
I just installed Ubuntu 9.10 via Wubi, but whenever I select Ubuntu from the boot menu,it automatically brings me right to a GRUB command line. I tried entering "boot", but it says the kernel is not loaded. What should I do not get this working? I've tried re-installing Ubuntu twice now, with the same results. My laptop is an HP Pavillion dv7-1020us, and my main OS is Windows 7. It's odd, but the Wubi 9.10 installation worked just fine on the same laptop when I was using Vista.

---

### Post by bcbc on 2010-03-01
Try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by garvinrick4 on 2010-03-01
Do you have the folder in C: drive called Ubuntu right next to Users? What is in folder?
In windows 7 CODE:  "bcdeit" without quotes and see if there is a Wubi attached to bootmanager.

---

### Post by amtur_poet on 2010-03-01
> **bcbc said:**
> Try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

Thank you very much! I tried this, and I was able to boot into Ubuntu. However, I'm having trouble setting up dual monitors and graphics card drivers. I made a separate thread about it here: [http://ubuntuforums.org/showthread.php?t=1419278](http://ubuntuforums.org/showthread.php?t=1419278)

---

### Post by bcbc on 2010-03-01
You're welcome. Good luck getting the monitors sorted.

---


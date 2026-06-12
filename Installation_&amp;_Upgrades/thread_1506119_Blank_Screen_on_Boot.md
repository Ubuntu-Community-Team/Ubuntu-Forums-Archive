---
title: "Blank Screen on Boot"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by grilldos on 2010-06-10
I set up a usb drive with a 10.04 image using Startup Disk Creator on my netbook running 10.04 netbook edition. Booting into it on my desktop originally took me to a blank screen after a purple holding image, but I was able to get through to the installation process (by first hitting F6 to get into the image's options menu) by adding "nomodeset" to the boot commands. The installation process went fine and I was given the usual "time to reboot" notification.

Of course, I can't boot into the installed OS as it just blank screens again. Holding shift during boot brings me to grub, but recovery mode also blank screens on me and I have no idea what to edit into the boot commands in grub so I can successfully boot into Ubuntu. The machine I'm running has an nvidia chipset, and I'm sure that's the cause of the problem.

I've tried numerous tips brought up in various forum posts across the web, but nothing I've found works for me. I can't even figure out how to load up a fully functioning terminal.

Any guidance would be very much appreciated.

---

### Post by confused57 on 2010-06-10
When you press shift & get the grub boot screen, press "e" to edit, then delete quiet & splash, add nomodeset, then press ctrl+X to boot.  If this gets you to a desktop, go to System--->Administration--->Hardware Drivers, then install the proprietary nvidia drivers.

Reboot & see if this works.

---

### Post by grilldos on 2010-06-10
That got me booted. I tried that previously, but I put nomodeset on a different line, which may explain why it didn't work. No matter, thanks man. Drivers installed, rebooting now.

Edit: We're in business. Hopefully this succinct thread will move up search engine cache to help every other dude out who ran into this.

---


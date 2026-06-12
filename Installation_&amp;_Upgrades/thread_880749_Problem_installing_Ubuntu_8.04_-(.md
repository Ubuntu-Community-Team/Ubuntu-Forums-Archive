---
title: "Problem installing Ubuntu 8.04 :-("
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by AtlDynasty25 on 2008-08-05
Hi all,
I am trying to install ubuntu 8.04 on my compaq v2000.  I burned the iso onto cd, verified it (it came out ok), and selected the install option.

Everything seems to go smoothly until after the ubuntu loading bar finishes.  At this point I receive the following error...

[348.693310] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[348.693424] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

This error flashes for a couple of seconds and then it proceeds to an orange screen with an artistic heron.  At this point it just stays on that screen.  The cd drive keeps spinning and nothing happens.  I let it go until my laptop power supply started getting way too hot (probably about 15 minutes or more)

What could be the problem?  I think the error has something to do with the built in broadcom wireless card, but that shouldn't affect the install, should it?

Thanks,
Matt

Oh, ps, i tried running ubuntu from the cd instead of installing and it does the same thing.  One window does actually come up with an error that i cannot recall, but i press continue, or ok, and it just shows the orange screen for 15 minutes again...

---

### Post by Pumalite on 2008-08-05
Burn a new CD at 4x after md5sum, check for CD integrity. Do not use CD-RW. Clean the lens in your burner and get wired to the Internet during installation. Preferably though a router providing you DHCP and a dynamic ip

---

### Post by renzokuken on 2008-08-05
I would be surprised if the wireless chipset was stopping the loading/installing of ubuntu. It seems to lock up when it tries loading the desktop.

Have you tried this CD on any other computers/laptops to check it? When it locks up, are you able to switch to a TTY terminal with Ctrl+Alt+F1? From here you could log in and run "dmesg" to try and diagnose the problem.

If you can't get the Live CD to work you could always try the Alternate CD (text-based installer) and see how that works.

---

### Post by AtlDynasty25 on 2008-08-05
Thanks for the help guys, unfortunately I just fried the laptop (lol).  I was taking out the ram to upgrade it and i dropped a screw in, and it sparked, and that's that haha.  I guess I'll try loading it on my desktop now.  I'm gonna have to clean up my windows partition tho and that may take a while.  Thanks again for the input and I'll be back in a couple of days maybe.  Thankfully the laptop is an antique and i'm not too concerned about it.

---

### Post by renzokuken on 2008-08-05
whoa that sucks...... i've fried a couple of desktops not being as careful as i should have.

good luck with the desktop

---


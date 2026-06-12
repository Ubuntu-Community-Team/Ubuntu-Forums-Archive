---
title: "Fresh built - can't boot to install or LiveUSB"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by blair-antcliffe on 2014-06-10
I just built myself a machine which is to be a dedicated HTPC. It has an MSI A78-E35 motherboard with A4-6300 APU. The machine POSTs just fine, and gets MSI's UEFI it detects the APU and memory just fine. All voltages are normal, and temperatures are around 35C for system, and 45 for APU.

I created a Ubuntu Minimal install USB using UNetbootin, on a 16GB Corsair USB 3 stick. Installation went without a hitch onto the SSD - lubuntu minimal. However, when booting, the screen is simply black, and sits there. Ctrl+alt+delete reboots the system, back to UEFI.

Next, I tried making a liveUSB of lubuntu - I could just remove packages I didn't need after install. When launching the installer, I see the launch screen, the installer loads up, the first menu appears briefly, then the system reboots - again, right back to POST. Likewise, when choosing to try lubuntu to install later, the desktop loads up for just a fraction of a second, and the system reboots.

Alright, maybe this is a problem with lubuntu. I tried the same thing next with xubuntu, with the same results. Installer loads then causes reboot, and running the OS from USB has the desktop load, then the system reboots.

Finally, I made a liveUSB of vanilla ubuntu. This one did somehow manage to boot all the way into the live mode, and stay at the desktop. Unity seems to work just fine. Next, I enabled the universe repository to install LXDE. I logged off, tried to start an LXDE session, and once again the system rebooted.

Finally, I tried the first step again using an older 4GB USB 2 drive, but got the same results once again.


So my question, given all of this, is what's going on? Why do LXDE and XFE seem to cause my machine to reboot, while Unity appears to work? How can I get around this to get a lightweight, minimal install?

Thanks for any help,

Blair

---

### Post by ubfan1 on 2014-06-10
Did you run any memory tests?  What do you see in any log files /var/log/...  Check the xorg.0.log (s) for any X problems. dmesg might output some errors of interest too.  syslog should have something.

---


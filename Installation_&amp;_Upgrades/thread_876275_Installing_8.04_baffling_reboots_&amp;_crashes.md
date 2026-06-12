---
title: "Installing 8.04: baffling reboots &amp; crashes"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by LyhjeHylje on 2008-07-31
I am trying to install kubuntu 8.04 into completely new computer. MB is gigabyte GA-MA78GM-S2H and has 3 sata disks (to be raided) one pata (for os) and usb dvd player.
I first tried the alternate cd and everything went fine until the first boot; it just wouldn't even try to boot, bios runs up to the point of handing over the control but there's no grub or linux messages.
Next I decided to try reinstall with the normal cd, that just hanged to 24% so I tried that "check cd"-option and got screenfull of "rejecting i/o to offline device" errors => stripped the sata cables off => lots errors about usb & hub (err -110) => took out the usb-dvd and hooked old ide cdrom instead.
Now the **BEEP** thing just reboots about every minute or two.

What can possibly be wrong with my setup?

---

### Post by LyhjeHylje on 2008-08-01
I tried with another ide cdrom, that one did not cause system to reboot but:
Alternate cd fails at installing base system, complains about corrupt files but cd integrity check says everything is ok.
Desktop cd freezes after I select language and select "install kubuntu", after long time it gives i/o error.
Next I tried installing from usb memory but my bios does not support them although it has long list of others: usb-zip/fdd/hdd/cdrom

---

### Post by LyhjeHylje on 2008-08-01
Update:
I tried with ubuntu 7.10 and the non-rebooting ide cdrom: after long loading I get errors about hdb, dma, i/o, "tray open" and whatnot.

Next I tried 7.10 with usb-cdrom and behold! Successful installation AND the system boots. 
Well, it does stop after "running local boot scripts" -line and I have to login and start X from command line. But at least this should mean my hardware is not broken, right?

---


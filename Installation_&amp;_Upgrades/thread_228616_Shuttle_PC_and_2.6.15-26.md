---
title: "Shuttle PC and 2.6.15-26"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by Mathachew on 2006-08-03
My company issues out Shuttle PCs with Ubuntu to run our web site. The latest kernel update for Ubuntu (2.6.15-26) causes these PCs to be erradic when booting up. I've even had some lock up whiel in use.

During boot up, the PC will freeze at different points of the boot up process; primarily at "Mounting root file system" and "Preparing restricted drivers". I have had no problems booting these up using 2.6.15-25.

At first I thought maybe it was if something was plugged into the USB port but have since seen these freezes occur with nothing but the essentials connected (power, mouse, keyboard, monitor & ethernet).

Any suggestions?

Edit: Also, the system will not restart properly when using anything above 2.6.15-23. The system will not restart properly; it locks up at "Will not reboot". I am unable to do anything with the keyboard at that point, such as pressing Scroll Lock twice to toggle PCs on my KVM switch.

---

### Post by Mathachew on 2006-08-03
I just noticed that there was an update for the latest kernel. I'll test it out and post my results.

---

### Post by Mathachew on 2006-08-03
I just tried the latest kernel update and am still having the reboot and start up issues with 2.6.15-26

---

### Post by casfindad on 2006-08-04
I too am having a problem with the latest kernel (2.6.15-26). My system is home-built, with an Athlon 3800 X2. Boot-up will freeze after the kubuntu progress bar is filled up. Booting into the 2.6.15-25 kernel works fine.

---


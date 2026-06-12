---
title: "EMERGENCY!!! Attempting Upgrade, System Frozen During Installation"
date: 2022-05-28
forum: Installation &amp; Upgrades
---

### Post by sasafrass452 on 2022-05-28
I'm attempting to upgrade to 22.04, & my system has frozen during the installation, which has already taken several hours. My mouse won't move, so I can't shut down properly. I'm afraid my old laptop will become an expensive paperweight. It's getting late here, & I can't leave it on all night since it's in my bedroom, & the light will keep me awake. Please help!!!

---

### Post by Frogs Hair on 2022-05-28
Did you create backups before you started and what are you upgrading from ?

---

### Post by sasafrass452 on 2022-05-28
I am upgrading from 21.10. I don't have a complete backup, a small number of files will be lost if I must install clean.

---

### Post by Frogs Hair on 2022-05-28
If the files are not that important I'd start with a clean installation. I have tested many upgrades and they should not take hours. What are the system specs ?

---

### Post by sasafrass452 on 2022-05-28
My laptop is a lenovo g50. I don't know the exact specs. Sorry!

---

### Post by guiverc on 2022-05-28
I don't have time for a detailed response... but if it was my machine

- I'd switch to text terminal and see what is happening...  I've had *release-upgrades* take up to 17 hours; and some steps can take a *long* time with no feedback, so patience is worth it.  Most *release-upgrades* don't that that long, but can still take hours (*varies on hardware, bandwidth & a lot of factors including what else you're doing on the machine*)

- I'd leave it on overnight..  see in the morning

- If you did need to re-install, you can boot a *live* system and copy/backup important files from there, and Ubuntu Desktop systems allow re-installation without loss of data, and will auto-reinstall *manually-installed* packages if available for the new release in Ubuntu repositories.   I use this feature to upgrade a number of systems instead of `apt full-upgrade`.. ie..  my regular re-install will upgrade my packages, achieves a QA (*Quality Assurance*) test so my music, non-default music player & other software I have installed is auto-installed anyway... ie. I use a QA-test install to upgrade the system & then continue to use it as if I just performed an upgrade.  Key is to **not format** as this is what triggers this type of ***upgrade via re-install***.  It works with `ubiquity` and `calamares` installers.

note: I didn't re-read this so sorry if it makes no sense, or errors are present; this also assumes a desktop system as data can be lost where server apps are involved.

---

### Post by sasafrass452 on 2022-05-28
As it is now, I would have to ask a friend to burn a disc for me, but I don't have enough room on my usb stick for all the files I'd need to save, since they are quite large. I can't leave my laptop on all night, since the light will keep me awake. I'll have to force it to shut down shortly, since there seems to be no other solution &#128534;

---

### Post by ActionParsnip on 2022-05-29
If you press CTRL + ALT + F1 can you drop to command prompt and use the system?

---

### Post by zebra2 on 2022-05-29
You should have a bios boot partition of 12meg (or similar) and an ESP partition (UEFI) of about 256meg. If you are using the Ubuntu partitioner they will format themselves. Both of these are needed regardless of whether the boot is UEFI or bios. In addition you will need a swap partition or a root partition large enough to accommodate a swap file. If you have those three things the install will work smoothly.  Or else just let the installer do it all as already suggested. I personally like to setup my own partitions. You can access your home partition with the installer and backup your data to a USB drive if you have one.

---


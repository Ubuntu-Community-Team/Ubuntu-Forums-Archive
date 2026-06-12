---
title: "No operating system found when installed new updates"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by geoff20 on 2020-05-03
Just clicked on install updates. Then asked to reboot and getting message that I do not have an operating system.
18.04LTS running on a NUC  DN2820FYKH. SSD containing operating system.
Backup on a USB.
Removed all devices and rebooted but still getting same message .

---

### Post by Impavidus on 2020-05-03
Can you boot a live disk? If so, try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), create a boot-info summary and show us the link. Don't run the recommended repair.

Boot-repair will give a lot of useful diagnostics in case of boot problems. We want to know the type of system (UEFI or legacy), the status of the boot loader, hard drive partitions etc.

Also, when you run your live session, you should be able to access the hard drive partition of your installed system. Look for the file /var/log/dpkg.log (this month's log) or /var/log/dpkg.log.1 (April's log) and find out which packages were upgraded when this problem appeared.

A regular upgrade isn't likely to cause a problem like this.

---

### Post by geoff20 on 2020-05-03
[http://paste.ubuntu.com/p/NBXSyChZy5]("http://paste.ubuntu.com/p/NBXSyChZy5/Did")/  Did a live install and ran Boot-Repair.Would not go past this and the info indicated that this could not repair my installation.When I tried to install Ubuntu I got the message that I only had 4 GB which is the size of the SD card.Seems to be not picking up the SSD (125 GB )Could be the problem

---

### Post by Impavidus on 2020-05-04
Indeed, your SSD isn't detected at all. That is a problem. Is the SSD detected in bios/uefi? Maybe a loose connector? Firmware problem? Other forum users may have some suggestions.

---

### Post by ActionParsnip on 2020-05-04
Is it a single boot (Ubuntu only) or is Windows here too?

---

### Post by geoff20 on 2020-05-04
Single boot.
Have  removed power from the SSD
Powered up into Bios and left for 30 mins.
Replaced  power to SSD and booted.
All working again but for how long!
Do I get another SSD or put it out to pasture.I think I bought it in 2015 and it's having problems running Kodi. Now have another box running CoreElec, Odroid N2 so don't really need it but loath to get rid of it.
Can you mark as solved

---

### Post by Impavidus on 2020-05-05
If it was just a loose connector there's no reason to assume it will get loose gain soon. But it could happen. And hard drives fail, both HDD and SSD. Just keep backups.

You can mark this thread as solved. Click Thread tools (near top of page), then Mark as solved.

---


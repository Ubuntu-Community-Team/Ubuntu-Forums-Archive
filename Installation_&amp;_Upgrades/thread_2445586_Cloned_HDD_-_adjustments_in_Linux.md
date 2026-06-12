---
title: "Cloned HDD - adjustments in Linux?"
date: 2020-06-16
forum: Installation &amp; Upgrades
---

### Post by Grigoriy on 2020-06-16
Hello!
                          Recently I found out that it should be OK for  me hardware-wise to clone the hard disk which contains my servers in it.  It's Ubuntu 16.04 (Desktop edition) The second part of my question (the  first one I asked in previous thread) is about OS. Linux that is... As  far as I know (and I'm no expert in the field)... if I make an image of  the whole disk bit by bit (Clonezilla), then I shouldn't worry about  making any adjustments in OS's config files. Provided that both drives  are identical, of course! So it's just kinda "Plug-n-play" thing. Would  be ready "out of the box", just to clone and that's it. Same disk as far  as OS is concerned. But I just wanna make sure... I'll attach two  pictures of disks with all the info about them.

---

### Post by oldfred on 2020-06-16
Are you keeping old drive?
You cannot have duplicate UUIDs (or GUIDs if newer gpt), so you have to unplug old drive.
You may also need to reinstall grub as MBR if BIOS or UEFI settings will not be updated with clonezilla.

---

### Post by Grigoriy on 2020-06-16
No I won't use them simultaneously. I would only use the newer one if the old one dies.

---

### Post by TheFu on 2020-06-16
I&#8217;m doing this now using ddrescue w/ some 4TB hdds.  The first has some relocated sectors and lots of read errors that are being corrected.  When I&#8217;m done, I&#8217;ll pull the old out of the array.  Because the drive wasn't dead and had just under 4TB of data doing a clone was easier than my normal restore process - which would also work perfectly, just with a little data loss from the few hours between the daily backup and when i pulled the drive out.

HDDs are 4TB w/ exactly the same number of sectors, same sector sizes, but one is an HGST desktop and the new one is a WD HC310 (data center) HDD w/ a 5 yr warranty, massive MTBF specs, and a few other specs that make it worth the higher price to me.
When the clone finishes any time now (5 hrs so far), i 100% expect it to boot and work as a replacement with no other changes.  in fact, earlier today i replaced all the SATA cables and can't say whether they are in the same slots they were previously. Doubtful, but that's why we use UUiDs and LVM mapper locations for storage.  i do expect to need to tell the bios which HDD to boot using, but that's it.

For backups, cloning like this is a poor choice. There are many better solutions with much greater flexibility that wouldn't waste an entire HDD.

---


---
title: "in need of installation help"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by threeRs on 2010-11-28
hey everyone, im completely new to linux. i wanted to install ubuntu on my laptop (hp pavilion zd8000) because it had some virus on it and wouldn't get past the "loading windows" screen.

i took the hard drive out, scanned it and backed everything up on my desktop, then reformatted the drive. i first tried reinstalling the hard drive and then starting the computer and trying to boot from usb, but that didn't work (it said something about a media cable missing i think. one important note: the cd drive in my laptop is dead, so i can't install ubuntu from that. then i took the hard drive back out, plugged it into my desktop, downloaded Unetbootin, and used that to put the .iso file onto the hard drive. i put the hd back in the laptop and it said "NTLDR is missing" and wouldn't start.

so i am stuck, and would greatly appreciate any help. i have tried reading tutorials on installing ubuntu to external hd's,  ubs sticks etc., but to no avail. thanks!

edit: my desktop is windows xp if that helps

---

### Post by threeRs on 2010-11-28
hey everyone, im completely new to linux. i wanted to install ubuntu on my laptop (hp pavilion zd8000) because it had some virus on it and wouldn't get past the "loading windows" screen.

i took the hard drive out, scanned it and backed everything up on my desktop, then reformatted the drive. i first tried reinstalling the hard drive and then starting the computer and trying to boot from usb, but that didn't work (it said something about a media cable missing i think. one important note: the cd drive in my laptop is dead, so i can't install ubuntu from that. then i took the hard drive back out, plugged it into my desktop, downloaded Unetbootin, and used that to put the .iso file onto the hard drive. i put the hd back in the laptop and it said "NTLDR is missing" and wouldn't start.

so i am stuck, and would greatly appreciate any help. i have tried reading tutorials on installing ubuntu to external hd's, ubs sticks etc., but to no avail. thanks!

---

### Post by sikander3786 on 2010-11-28
Burning the image to the hard drive is no way the proper way of doing an install. It won't save any configuration you make later.

Please check the image's MD5SUM first.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn it to USB device using unetbootin. Make sure your USB drive is formatted FAT32 and not NTFS.

Change the boot order from Bios and make your USB device, first boot device.

It should boot now, if it doesn't, please post back with some more details.

---

### Post by cariboo on 2010-11-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by oldfred on 2010-11-28
If you can plug drive into your desktop just install from there. Just do not install any proprietary video drivers and it should boot just find when plugged into your portable.

---


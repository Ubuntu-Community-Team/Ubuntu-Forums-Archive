---
title: "configuration apt hangs at alternative cd installation"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by sonicgg on 2008-11-13
I again have problem on installing 8.10. 

I use alternative cd, coz live cd is not suitable for me for some reasons:)

when starting installation from cdrom, everything goes right, partition, install base system, then it hangs at 'configuartion apt', the screen shows 'scannning cdrom' , hangs at 12% even after 8 hours...

I googled, got some hints, I skipped the configuration apt step, go directly to install grub. then everything seems ok... i can boot from the new system.

the problem is the new system only contains base system, no X, no gui...then i want to use api-get to install stuff from cdrom.. but when i execute: 
     sudo apt-get install *** the system hangs
then i found cdrom is not mount.. then i executed: 
     sudo mount -t iso9660 /dev/cdrom /media/cdrom1 the system hangs again..


so i have no way to install the other stuff except the base system...
actually I can install them from network, i never tried this.. coz i think it's not a good solution...

can someone help me?

---

### Post by sukhhari on 2008-11-13
There are two things to do?

1. Checkout your CD/DVD may be problem while make into ISO .
2. Either you remove your Network Cable.

:mad:

---

### Post by sonicgg on 2008-11-14
i burn with a mac pro, it will verify after burning...so i don't think there's any problem in cd...

ive already remvoed the cable.....still no luck..

---


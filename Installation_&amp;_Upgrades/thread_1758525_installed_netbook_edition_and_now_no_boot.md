---
title: "installed netbook edition and now no boot"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by cyberthug47 on 2011-05-14
hello all, ive never tried to do a linux installation like i just did and it has obviously failed. heres the situation. asus eeepc w/16gb ssd drive and 16gb sd card. i had windows installed on the ssd. last night i installed ubuntu netbook ed. from live flash drive to the sdcard. upon installation finishing then rebooting all i get is a black screen with a flashing cursor. i assume grub is messed up and the type of install i did probably wasnt wise lol. im not super proficient at linux but know enough to make me dangerous lol. is there a command line i can use to repair this problem via rebooting from the live flash drive? or am  i better off booting from windows cd, and repairing the mbr on the windows side and just keep using a live flash when i want linux? thank you in advance.

---

### Post by dabl on 2011-05-14
In my Eee PC 4G/701, the SD card drive is actually a USB device.  So booting from the SDHC card is exactly the same process/problem as booting from a USB stick.

Yes, I would advise you to "fix MBR" with your Windows CD, and then if you want to install Linux on the SDHC card, check out how to set your Eee PC to boot from USB device.

---


---
title: "Installation problems with Vulcan Flipstart"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by luthiensdad2 on 2015-11-30
Hello, I'm trying to install Lubuntu 15.10 on to my Flipstart UMPC, currently running WinXP SP2, I'd like to install it alongside so as to be able to dual boot. There is scant documentation online for this device but I have found that it should be able to install Linux.

None of my attempts so far have been successful however. I have tried first to install from usb stick using Universal USB installer 1.9.6.2 & XBoot 1.0 to create a bootable .iso file on it, but neither of these are detected by the bios as a bootable drive on startup. The stick DOES show up in "my computer" under dive letter D: as a "device with removable storage" (where system drive is C: ) & I can view the files in explorer. I changed the boot order in the bios to boot D: first & C: 2nd but it just boots right into XP. 

The choices in bios for D: are: 
"Floppy 0",
 "USB Floppy", 
"Ide 0/Pri Master"
"Ide 1/Pri Slave"
"Ide2/Sec Master"
"Ide 3/Sec Slave"
"USB Hard Drive"
"None"

the bios default setting for the system drive C: is "Ide 0/Pri master". I have not changed it. I have tried booting the stick by selecting all of the above options for D: w/o success. I should also mention that I am using a micro sd card in a usb adapter. Can anyone offer any suggestions as to how I might proceed? Feeling pretty stupid right now.

---

### Post by Vladlenin5000 on 2015-11-30
Hi and welcome.

My first suggestion is to NOT even try a dual-boot because the 30GB you have are barely enough for Windows alone.

Now, regardless of such limitation, you should be able to boot from a USB flash drive anyway. If you can't then either your setup (SD + USB SD card reader) isn't supported by the BIOS (most likely) or it does but somehow you did something wrong when creating the installation media.

---


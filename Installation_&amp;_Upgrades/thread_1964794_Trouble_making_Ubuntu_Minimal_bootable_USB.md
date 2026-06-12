---
title: "Trouble making Ubuntu Minimal bootable USB"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by mihalybaci on 2012-04-24
The other day I attempted to perform a Ubuntu minimal install on my laptop using a USB. Startup Disk Creator would not let me select mini.iso for some reason, so I used the following command:
```
sudo dd if=mini.iso of=/dev/sdc bs=4M; sync
```
No errors were given, the USB booted fine and I began installing. At the grub install stage, I got the error message: "Unable to install GRUB in /dev/sdb. Executing 'grub-install '/dev/sdb' failed. This is a fatal error."  Then the computer wouldn't boot, so I gave up and used the same 'dd' command to install CrunchBang, and everything went flawlessly. Do I have to burn the mini.iso to a CD? Or is there some other trick to making a minimal USB?

---

### Post by nothingspecial on 2012-04-25
*Thread moved to **Installation & Upgrades**.*

See if it does better here :)

---

### Post by 5circles on 2012-04-29
I'm having the same problem with "Executing 'grub-install '/dev/sdb' failed. This is a fatal error."

I'm not trying to create a full system on a USB flash drive, just a boot loader.  The rest of the system is on other hard drive partitions.

I reformatted the USB flash drive to FAT32 following instructions in one thread.  No difference and this didn't seem necessary from what I read elsewhere.

Then I ran grub-install from a different Ubuntu system with no error.  Same error message from the installing Ubuntu system.

Tried a different flash drive - same problem.

Any ideas?
TIA

---

### Post by 5circles on 2012-04-29
Managed to find a larger USB flash drive (actually an SD card in a USB adapter), and installed to that successfully.  Rebooted OK.

Still hoping to solve the USB flash as boot only issue.

---

### Post by mihalybaci on 2012-05-02
I'm not trying to install to the USB, I was just trying to create a bootable USB to install on my laptop, which it sounds like you're trying to do too. I've successfully created a minimal install as a Virtual Machine before, but that was straight from the .iso in my downloads folder not from a USB. I still haven't figured out the main problem either.

---

### Post by 5circles on 2012-05-02
I'm not sure if this will help, but it might give you some ideas. [http://ubuntuforums.org/showthread.php?t=1970596](http://ubuntuforums.org/showthread.php?t=1970596) 

I've concluded that the oldest Flash drive I was trying to use was faulty or incompatible.  The one that is working I thought hat the same error message at one time, but after numerous experiments formatting and repartitioning, it is working.  Sorry I can't tell you more about exactly what worked.

--Mike

---


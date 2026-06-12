---
title: "Cannot boot after upgrade to 14.04"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2014-06-07
It seemed all OK after upgrading. I worked with 14.04 already one day, but then I had to turn off the machine and since then it cannot boot anymore.

I get the following screen:

> 
Gave up waiting for root device  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/ede9ffb0...... does not exist
Dropping to a shell!

BusyBox v.1.21.1 (Ubuntu 1.1.21.0-ubuntu1)built in shell
Enter 'help' for a list of built-in commands
(init/rams)


cat /proc/cmdline
Boot_IMAGE=/dev/vmlinuz-3.13.0-29-generic root= UUID=ede9ffb0..... ro quiet splash


Please note, this computer has TWO 3 TB hard disk, same manufacturer. So it seems, grub has some problem to get the right device.
I wonder, that it could boot after the upgrade was completed, and now not anymore.

How to fix it?
(I miss to work with MY computer, please help me soon ;-)   )

---

### Post by ELMIT on 2014-06-07
I unplugged the second 3TB hard disk, and now it can boot.
I got a lots of data on this hard drive, how can I add it again safely?

Looking now in /etc/fstab I see that disk/by-uuid number. It seems somehow it got confused with the other hard drive

Grub problem comes into my mind, but how to tackle that down?

---

### Post by LastDino on 2014-06-07
Is the problem repeating itself after you plug that HD in?

---

### Post by ELMIT on 2014-06-07
Yes, it is exactly the same, when I plug in the 2nd hard disk, then it cannot boot, as reported above, when I unplug it works again.

---

### Post by LastDino on 2014-06-07
This is shot in the dark and probably wont work, but unplug that 3TB and boot up with the HD which has Ubuntu on, then reinstall the grub and see if the problem persist.

---

### Post by ELMIT on 2014-06-07
Yes, it is exactly the same, when I plug in the 2nd hard disk, then it cannot boot, as reported above, when I unplug it works again.

---

### Post by ELMIT on 2014-06-08
I downloaded the Boot-Repair disk and plugged in BOTH hard disks to repair.

After rebooting the system, it is still the same, so I have to unplug again the second hard disk.

Boot-Repair posted at [http://paste.ubuntu.com/7616069/](http://paste.ubuntu.com/7616069/) the result.
Any thoughts?

---


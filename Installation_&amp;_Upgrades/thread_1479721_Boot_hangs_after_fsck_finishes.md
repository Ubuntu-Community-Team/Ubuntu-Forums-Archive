---
title: "Boot hangs after fsck finishes"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by thenuge26 on 2010-05-10
I just installed 10.04 from the minimal install cd (twice), and when I boot it up, it runs fsck on the 3 partitions, shows they are clean, and then nothing.  I can't even get to recovery mode.  I had previously installed 9.10 fine on this computer.  

I can't even find out what the real problem is, even with the quiet splash disabled.  It just stops after successfully running fsck.

Any help is appreciated.

Thanks

---

### Post by n3rdnl on 2010-05-30
Did you find a solution yet? 

I have exactly the same problem, installed ubuntu 10.04 64bit twice and it runs great for some time and then... it hangs during boot after fsck.

Edit:
I might have found a solution (at least in my case). 
The problem seemed to be the auto mounted drives (that were not preset at the time the problem occurred). 
So i placed the drive in an other machine (vm in this case) and commented out all the non-default auto mounts in /etc/fstab . After that the vm booted again, but this does not seem to be expected behavior to me.

---

### Post by kirel on 2010-07-08
Running 10.04 64 bit version.
Problem appeared after configuring mount point and settings for external usb drive. The system hangs only when the external usb drive is off.
Solved by commenting the corresponding line in fstab.

---

### Post by n3rdnl on 2010-07-10
> **kirel said:**
> Running 10.04 64 bit version.
Problem appeared after configuring mount point and settings for external usb drive. The system hangs only when the external usb drive is off.
Solved by commenting the corresponding line in fstab.

In case of an usb drive, you could use the noauto mount option.

---

### Post by thejaswi on 2010-08-14
In my case i didn't have an entry in /etc/fstab for usb drive mount. But by deleting the directory /media/external where i mounted my usb drive last time, fixed the issue.

---

### Post by Bobulous on 2010-08-14
Just in case it helps anyone who has the same problem as described by the OP, you might want to see this thread:

[http://ubuntuforums.org/showthread.php?t=1521853](http://ubuntuforums.org/showthread.php?t=1521853)

In my case the problem was caused after an upgrade to the latest kernel, and it turned out to be my RAID array not mounting automatically. If you're using mdadm to mount RAID volumes, it might be worth a look.

---


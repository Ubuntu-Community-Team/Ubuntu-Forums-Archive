---
title: "Now nothing boots"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by telcomguy on 2005-08-04
Ok, I'm new  to this, so please "talk slowly".  I have a new HP PC running Windows XP home edition.  I connected a USB hard drive and loaded Kubuntu on it. Since I wanted the choice to boot into either OS, I loaded grub.  This completed the first stage install.

I restarted the PC for the second stage and the grub menu appeared.  I chose ubuntu and got the following message:

root  (hd1,0)
 filesystem type is fat, partition type 0xc
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 ro quiet splash

Error 15: File not found

Press any key to continue...

When I pressed a key, the grub menu reappeared.  I tried to boot into XP and got the following message:

root  (hd0,1)
 filesystem type unknown, partition type 0x5
savedefault
makeactive

Error 12: Invalid device requested

Now I'm stuck.  Any help would be greatly appreciated.

---

### Post by orev on 2005-08-04
This could be the complete wrong answer, but one that should work for you. (?)

When you tried to boot into Kubuntu, for whatever reason, grub looked to a fat file system - which is for Windows.

It appears that something went funny with your installation...

If it were me, I would use the system restore disk sent by HP (or using the system restore from the Bios screen, F10 on boot, I think.)

Then once you had the system back to stock, I would install Kubuntu on a partition in the internal hard drive. Then if you need more storage for both operating systems, I would partition the USB drive - otherwise you could just leave the USB drive alone (fat file system, or format it for linux).

I don't think that you will be very happy with the performance of any OS loaded from a USB cable....

Just my 2 cents.... hope it helps.

---

### Post by telcomguy on 2005-08-04
Thanks for the suggestion.  Believe it or not, my PC came with XP preinstalled and with no restore disk.  When I tried F10, it ran grub with these messages:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

...and then it hangs.  

I appreciate your responding in any case.

---


---
title: "Two Identical 1U Servers Grub Error 18"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by shade6789 on 2007-11-04
I have a 1U with ubuntu installed on with no problems. Has been running solid for about a month.  I just purchased an identical server (same hardware, bios revision, etc...) and tried to put a fresh install on it.  (It came shipped with Fedora (Working))

I install the same way I did with the previous server putting grub on HD0 by default.  I am getting a Grub error of 18.  I checked the drives both PATA set to cable select.  LBA is enabled in bios.  Booted to the liveCD and tried to do setup(hd0), but grub doesn't seem to recognize the drives.  But I can mount and use them on the liveCD.

Let me know if you need more info, but I'm really confused since I have two identical units with the same bios setup and drives.


Thanks in advance!


UPDATE:

Did a reinstall and observed the results.  

grub-install (hd0) installs successfully...  /boot/grub/...  is located on my root partition like it is on the working box.   When I go into grub and try to do a find I get "File not Found" and also try to do a root (hd0,0) and I get "Selected disk does not exsist"   

If it can see the drive during install of grub why can't it after?


UPDATE 2 (RESOLVED):

I'm not really sure why since my first server didn't need this but I created a partition mounted as /boot at the beginning like you would have to do on older machines and it worked.

---


---
title: "dpkg interruption error - can no longer update"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by grits on 2008-03-03
During a normal software upgrade, I experienced an unrelated to the update system lockup. The system was hardlocked with no visible indication of any activity. After a period of time, the system was reboot. Now whenever an attempt os made to run a software upgrade of any form, the following message appears:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Attempting to run the dpkg command above results in :
# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-initrd-2.6.18.8.tex5.img
Cannot find /lib/modules/initrd-2.6.18.8.tex5.img
update-initramfs: failed for /boot/initrd.img-initrd-2.6.18.8.tex5.img
dpkg: subprocess post-installation script returned error exit status 1

This is a dual boot system with Ubuntu and PCLinuxOS installed - which is where the reference to "tex5" in the preceding message comes from.

I can't figure out how to fix this error.
Any suggestions?

Thanks!

---


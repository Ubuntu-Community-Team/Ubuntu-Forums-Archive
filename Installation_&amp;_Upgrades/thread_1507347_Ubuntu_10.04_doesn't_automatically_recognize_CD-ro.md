---
title: "Ubuntu 10.04 doesn't automatically recognize CD-rom &amp; USB after update from 9.x"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by rbhausoul on 2010-06-11
Hi,
Someone gave me an Ubunto-CD and it worked great. So I installed it and updated it to Ubuntu 10.04. But now my CD-rom and USB-drive are not auto-mounted.

When I use pmount /dev/sdb1, I can manually mount the USB-drive. There is also a folder named 'sdb1' in /media. But till now I didn't found a resolution to my problem by Googling for it.

Also my windows-partition was not show in Ubuntu 10.04 but this I could fix with NTFS Configuration Program. So this part has been solved. I'm now only searching for a way to set my CD-rom and USB auto-mount.

Who can help?

---

### Post by efflandt on 2010-06-11
You do not give any clue what hardware you have.  I had that problem (and suspend/hibernate issue) on an old Dell Inspiron 8200 laptop.  It had a hot swap drive bay that had a DVD drive in it.  But apparently because it could be hot swapped, Linux kept polling for a floppy drive, resulting in log errors attempting to read fd0, lack of auto mounting USB or CD/DVD's, and failed to suspend or hibernate because it could not put udisks-deamon to sleep, which kept polling for the non-existing floppy.

So if you have no floppy and are getting any fd0 errors in dmesg or /var/log/messages similar to "end_request: I/O error, dev fd0, sector 0", either disable the floppy in your BIOS, or if that does not work:

Add following to /etc/modprobe.d/blacklist.conf (use **sudo** or **gksu** to run your editor):

blacklist floppy

Then do: **sudo update-initramfs -u**

Then reboot and see if USB and other removable media auto mounts when inserted.

Note that other partitions on internal drives are not auto mounted unless you make proper mount points (usually in /media unless you want it mounted elsewhere) and entries in /etc/fstab (preferably using UUID).  Although, they will mount if you have permission and select them in Places.

---

### Post by rbhausoul on 2010-06-12
Thanks!
This worked

---


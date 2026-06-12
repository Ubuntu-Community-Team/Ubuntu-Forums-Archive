---
title: "USB flash won't boot but runs fine when booted from HDD (error 21)"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by lotus49 on 2008-04-05
I have recently installed 7.10 on a Lexar 8GB Firefly USB flash disk.  I have installed 7.10 to USB flash drives successfully at least 20 times so I do know a reasonable amount about the process and installing grub manually (some changes to menu.lst at least have been required every time).

When I boot from the flash drive I get grub error 21.  However, I have edited the menu.lst on the internal HDD of the laptop I am using and the installation boots and runs fine when the initial boot is from the laptop.

For some reason, during the installation, grub was installed to the laptop's HDD and I was not given the option to install it to the flash drive.  No matter, I thought as this has never worked properly anyway so I tried reinstalling grub (both using grub-install and manually using the grub command line) but this has made no difference.

I have tried installing Damn Small Linux using syslinux and that worked fine so there doesn't appear to be anything wrong with the drive.

Any suggestions would be most appreciated.

---

### Post by Pumalite on 2008-04-05
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
Your Grub got half installed in your HDD and the other half was installede to the USB. If you installed with Live CD, at step 8, go to 'Advanced Tab' and you can change (hd0) for /dev/xxx
Where xxx is your USB.

---

### Post by lotus49 on 2008-04-05
Thanks for the response.  I had a look through that and realised that the UUIDs were wrong in menu.lst (I hadn't had this happen before).  I noticed this after I decided to try to boot the USB flash drive on another laptop (I still got error 21) so I corrected it and bingo, it worked.

However when I tried back on the first laptop, I still got error 21 so there appears to be more to this than meets the eye.

Since my problem has changed I'll start another thread.

---

### Post by Pumalite on 2008-04-05
Good luck.

---


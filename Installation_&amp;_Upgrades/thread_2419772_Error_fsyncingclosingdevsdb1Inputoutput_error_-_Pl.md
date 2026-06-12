---
title: "Error fsyncing/closing/dev/sdb1:Input/output error - Please Help"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by genz on 2019-05-25
I recently had to reinstall my win/ubuntu dual install. Once I installed windows and made a ubuntu usb , every time i try to install I get Error fsyncing/closing/dev/sdb1:Input/output error
I tried 1. Checking health of disc drives. All were fine and good. I then checked physical drive connections and they were fine. Every search kept tellingme it was a hardware error but all tests show there to be no problem .

---

### Post by dino99 on 2019-05-25
Entries from /etc/fstab need to match 'sudo blkid' output (uuid)

what kind of hardware is sdb1 ? if it's a movable one, then each time you plug it , you will get a new uuid.

---

### Post by genz on 2019-05-25
It's a Seagate 1t hard drive and a 500g generic hard drive. Both scan as in good health. Neither have any problems getting flagged when I run checks on them.

---

### Post by Rubi1200 on 2019-05-25
Have you tried the liveUSB on another computer, have you verified the image was good when you burned it?

If you can, try downloading and burning another ISO to another stick.

I prefer using Rufus but there are other good tools out there too.

---

### Post by genz on 2019-05-25
Have tried Ubuntu 18.04 and Linux Mint 19.1. Checked each before using them. Everything checked out. both ran into same problem .

---

### Post by Rubi1200 on 2019-05-25
Not sure what to suggest except perhaps check SATA mode in BIOS and change from IDE to AHCI and then see if the Ubuntu USB is picked up and can install.

Other than that, there might be some underlying failure going on that was not necessarily picked up by SMART tests.

---


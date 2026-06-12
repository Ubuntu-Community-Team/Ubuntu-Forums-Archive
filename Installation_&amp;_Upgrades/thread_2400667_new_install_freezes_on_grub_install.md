---
title: "new install freezes on grub install"
date: 2018-09-08
forum: Installation &amp; Upgrades
---

### Post by buckey2 on 2018-09-08
I have been trying to install 18.04 on my acer es 15 laptop with windows 10. all goes well until the grub tries to install. it freezes up and I have to do a hard reboot. I have also tried to install MX 17 with the same results. I have disabled quick start in windows. ESP was selected to install grub2 to. doing some more reading, I'm guessing this may be because of windows secure boot. if this is the case, and I reload windows, will it let me to disable the secure mode? also are there any other ideas?

---

### Post by yancek on 2018-09-08
You should be able to disable SecureeBoot in the BIOS.  It isn't necessary to do so with Ubuntu.  Acer has a requirement that you set "trust" in the BIOS before you can install a new system.  I would suggest you check the BIOS or look at the user manual for the machine.  If you don't have one, you should be able to find one online with the specific model you have.

---

### Post by buckey2 on 2018-09-09
Thanks yancek. I disabled the TPM (trusted platform module) and it didn't help. I've got lots of time, will keep searching to see what will work.

---

### Post by oldfred on 2018-09-10
Its not TPM.

All Acer's seem to have the same "trust" requirement. 
And many have to have an UEFI update from Acer.
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---


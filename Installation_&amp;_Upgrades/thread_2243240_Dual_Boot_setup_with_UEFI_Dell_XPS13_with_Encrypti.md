---
title: "Dual Boot setup with UEFI Dell XPS13 with Encryption"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by brooklynzoo81 on 2014-09-07
Hello all.  

I recently was able to install windows 8.1 x64 via UEFI with Bitlocker.  I shrinked the partition down to give space for Ubuntu about 100 gigs out of a 256GB SSD drive.  I am not very familar with Ubuntu nor UEFI i was able to get lucky with that part.  I would like to have a dual setup on this Dell XPS 13.  My question would be how would i go about dual booting these two operating systems if bitlocker is in play?  I would also like to encrypt Ubuntu as well if possible.   Any help with this would be greatly appreciated on this matter.

---

### Post by brooklynzoo81 on 2014-09-08
Ok i have managed to install ubuntu 14.04 with secure boot on.  However when i click on windows which is one /dev/sda2 efi, i get the following in the image. [http://postimg.org/image/m39m5bjq9/](http://postimg.org/image/m39m5bjq9/)  When i disable secure boot both operating systems work fine.  Is there a way i can keep secure boot on and get windows working again??    Also note that i have bitlocker enabled on the windows partition, thanks.

---

### Post by oldfred on 2014-09-08
With secure boot on can you boot Windows directly from UEFI menu or from one time boot key, often f12 but may vary?

There is or was a bug in grub chain loading Windows 8 with secure boot on. But you still should be able to boot directly.

 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

### Post by brooklynzoo81 on 2014-09-19
I think i am going to leave it with secure boot off for now.  I am tired of repairing windows every time i turn secure boot on.  Hopefully a later release will resolve this issue.

---


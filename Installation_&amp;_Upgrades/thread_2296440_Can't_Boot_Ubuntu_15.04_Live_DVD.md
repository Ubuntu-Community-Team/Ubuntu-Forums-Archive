---
title: "Can't Boot Ubuntu 15.04 Live DVD"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by willygatti on 2015-09-25
I recently purchased a HP laptop computer with Windows 10 pre-installed on it, and I would like to install Ubuntu 15.04 on it.  After disabling secure boot and fast startup, I was able to boot into the Ubuntu grub menu and I selected try Ubuntu without installing.  Unfortunately, Ubuntu booted with a blank screen after that instead of the live desktop environment.   I then tried re-downloading Ubuntu 15.04 and burning the disc image to a fresh blank DVD which gave me the same results.  How do I install Ubuntu 15.04 on my new computer?

---

### Post by michael308 on 2015-09-25
Try F11 on boot up

---

### Post by ubfan1 on 2015-09-25
Seems like a video problem. What video chip is used, like Nvidia, ... some other proprietary etc.  The first boot may need additional kernel parmeters, available from the function keys at the DVD menu (Try, Install, ...) -- Try the "nomodeset" option.  If that works, you can then install the proprietary driver for better performance.

  Also, check some things before trying the install:
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or hardware problems.

---


---
title: "can''t boot kernel - error 15"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by carpman on 2010-08-07
Hello, ok had an issue after update in the nvidia module was not loading, after much messing about i found that system had installed kernel 2.6.32-24 but this had been added to grub even after running update-grub even though kernel was in /boot ?

It was booting into 2.6.31-17 fine

i removed 2.6.32-24 with apt-get remove and then reinstalled.

Now on reboot i can menu entry for 2.6.32-22/24 and 2.6.31-17 but none will load, just error 15 file not found?


Am going to try booting live cd and doing update-grub again but not sure if this will help?

any ideas?

---

### Post by carpman on 2010-08-07
hello, ok tried editing grub menu and removed UUid line and replaced with

root (hd0,0)

Also edited kernel line and replace UUid with /dev/sda1


Drive only had sda1 plus swap partition.

This will allow a  boot but will not mount /


This starting to  peeve me, any ideas?

cheers

---

### Post by carpman on 2010-08-07
ok booted into live cd and chrooted into install and removed and reinstalled grub, followed error 15 guide in ubuntu docs but still the same error 15?

Going to try apt-get install grub2 as original install was 8 version and upgrades may not have correctly installed grub2.

---

### Post by confused57 on 2010-08-07
> **carpman said:**
> ok booted into live cd and chrooted into install and removed and reinstalled grub, followed error 15 guide in ubuntu docs but still the same error 15?

Going to try apt-get install grub2 as original install was 8 version and upgrades may not have correctly installed grub2.
Sounds reinstalling grub2 should be the "fix":
[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29](https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29)

---

### Post by carpman on 2010-08-07
ok did this and had small error with data mount options need to set it writeback but at last can now boot in gui :)

---


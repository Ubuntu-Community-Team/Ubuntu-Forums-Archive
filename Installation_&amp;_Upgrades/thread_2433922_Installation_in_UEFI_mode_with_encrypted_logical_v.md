---
title: "Installation in UEFI mode with encrypted logical volumes"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by yrtnsky on 2019-12-27
Hi!
Is there any way to install Xubuntu with manually created logical volumes on encrypted partition? How to make it bootable after such installation?
On attempt to create encrypted partition only "physical volume for encryption" option is available. After that appears only 1 encrypted volume and nothing else can be changed, while I want to have at least /root and swap volumes.
After automatic installation hard drive disappears from available boot devices, boot-repair can't fix the problem. Just copying files to BOOT folder on EFI partition also does not help.
I was thinking that after Debian it will be much easier to install Xubuntu, but it looks like I was wrong.
Thank you

---

### Post by TheFu on 2019-12-28
The root LV is usually huge post install, so huge as to be a problem.  Immediately post-install, reduce the root LV, then create LVs for other needs inside the encrypted partition as needed.  Unfortunately, the forum search doesn't work for terms with a dash (-) inside, which means search for prior posts with my specific, encrypted, LVM on UEFI, storage layout is difficult. 

Found it: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
That was a standard install, just checkboxed whole disk encryption with LVM.

---


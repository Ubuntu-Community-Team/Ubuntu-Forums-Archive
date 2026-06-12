---
title: "Boot-repair stuck on unhide"
date: 2019-06-04
forum: Installation &amp; Upgrades
---

### Post by janw-oostendorp on 2019-06-04
The  FN brightness keys don't work on my laptop, So a while back I [askedUbuntuSe]("https://askubuntu.com/q/1093016/208343") someone with the same laptop did not have this problem.
I upgraded from 18.04 to 19.04 through a reinstall, still no FN keys.

So I tried a boot repair form a usb stick. But that boot repair gets stuck on "unhide boot menu". 
Below my pastebin, what can I do next?
I don't mind going nuclear and do a full (grub?)reinstall.


[https://paste.ubuntu.com/p/b8MFKYYdqp/](https://paste.ubuntu.com/p/b8MFKYYdqp/)

---

### Post by oldfred on 2019-06-04
Function key issue should not be related to any boot issues.
Also Boot-Repair wants to reinstall grub to ESP on sda, but you must have grub in ESP on the NVMe drive which the report only partially shows.

Better to post a thread with model system and function key issue in title, so those familiar with those issues may respond.

---


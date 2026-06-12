---
title: "Why does re-boot fail on login?"
date: 2023-02-12
forum: Installation &amp; Upgrades
---

### Post by victor2preston on 2023-02-12
I made a change in fstab and the reboot failed, so I did a safe boot and changed the fstab back the way it was but stil lit fails, but now only after I try to log in to the user account. Analysis at [https://paste.ubuntu.com/p/jKg45Zss8](https://paste.ubuntu.com/p/jKg45Zss8)

---

### Post by deadflowr on 2023-02-12
Your paste is not found.

post your fstab

---

### Post by ajgreeny on 2023-02-12
Unfortunately your pastebin link is not leading anywhere.
Can you please boot to a live system from USB, as I presume you did to create what I assume was the boot-info report.

It may also help us if you can show us the content of your installed OS's /etc/fstab file by clicking on the root partition in the left hand pane of your live system's file manager.
Please also show the output of ```
sudo blkid -c /dev/null
``` so that we can compare the UUIDs of the partitions and make sure they are correctly shown in fstab. 
Any discrepancies between the two would be why you can not login successfully.

---


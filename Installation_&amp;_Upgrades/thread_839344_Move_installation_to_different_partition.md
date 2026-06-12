---
title: "Move installation to different partition"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by simvin76 on 2008-06-24
Hello

If I want to move my installation from 
/dev/sda3 to
/dev/sda5

Is it enough to change in */etc/fstab* and in the kernel line in */boot/grub/menu.1st*?


Best regards
/Simon

---

### Post by diaa on 2008-06-24
As far as I can tell you can only do this by copying the data from this partition to the other partition, probably using *partimage*, /dev/sd* are hardware devices and you can't change them(i.e. /dev/sda1 refers to the first partition on the primary master harddrive, there's no way to change this)

---

### Post by simvin76 on 2008-06-24
I meant to copy with all permissions (cp -a) from /dev/sda3 to /dev/sda3. I don't want to change /dev/sd**x** (but I think you can do that with udev-rules).

fstab is mounting /dev/sda3 on '/', I have to change that, as well as changing from what partition the system should boot.
My question was if that was enough when moving the system.


Best regards
/Simon

---


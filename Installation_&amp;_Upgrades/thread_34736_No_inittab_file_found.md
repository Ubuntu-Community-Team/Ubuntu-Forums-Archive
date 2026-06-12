---
title: "No inittab file found"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by shady on 2005-05-16
I'm trying to install ubuntu on AMD64 (dual boot with win2k3).
w2k3 in on SATA, linux is on IDE.

after 1st boot, GRUB was unable to find my IDE on (hd0,2), changed to  (hd1,2) fixed that ... but right after user/pass screen ubuntu froze.

now if I try to boot to linux I get :

 "enter runlevel:" and "no inittab file found" 

in recovery mode when I try to "mkdir" or "cp"  I get "error ... read only file system" ?! 

cant find anything wrong in the logs (the ones I've looked at so far).

-----------
AMD64 3000+ 1GB
80 SATA, 60 IDE

---

### Post by lao_V on 2005-05-16
what's in your /etc/fstab file?

---

### Post by shady on 2005-05-16
Thanks for the fast reply,

fstab :
---
proc              /proc    proc    defaults  0    0
/dev/hda3    /           ext2    defaults, errors=remount-ro 0
/dev/hda6    none    swap
.
.
.
--

GRUB - recovery:
---
root (hd1,2)
kernel /boot/vmlinuz   root=/dev/hda3  ro console=tty0 single 
---

as my system appears to be RO I cant edit fstab.

---


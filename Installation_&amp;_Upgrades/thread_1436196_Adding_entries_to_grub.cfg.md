---
title: "Adding entries to grub.cfg"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by ulriksvensson on 2010-03-22
Hi all. 

I've just installed Fedora 12 on a partition on my harddrive. Ubuntu 9.10 is installed on sda1, and Fedora on sda3. When I execute update-grub Fedora is not added to grub.cfg. How do I add Fedora to the boot menu? Since the file grub.cfg is read-only I don't know how to do this.

---

### Post by phillw on 2010-03-22
hi,

a quick one to check, did you use ```
sudo update-grub
``` ?

grub should 'see' your Fedrora. However, if you installed Fedora after ubuntu, chances are Fedora has over-written grub2.

If using sudo does not work, head over to #13 of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and pop Grub2 back on.

Regards,

Phill.

---

### Post by oldfred on 2010-03-22
If the update grub does not find it, you have to add it to 40_custom and run the update grub.

[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

---

### Post by ulriksvensson on 2010-03-23
How do I get all numbers here:
 
```
search --no-floppy --fs-uuid --set 2c905a01-e585-4fc4-a087-c86153590eff
    linux    /boot/vmlinuz-2.6.31.12-174.2.3.fc12.x86_64 root=UUID=2c905a01-e585-4fc4-a087-c86153590eff ro   quiet splash
    initrd    /boot/initramfs-2.6.31.12-174.2.3.fc12.x86_64.img
```

---

### Post by oldfred on 2010-03-23
If you are asking about the UUIDs.

sudo blkid will show the UUID for each partition.

All the other numbers are the versions of your kernels.

---

### Post by ulriksvensson on 2010-03-24
> **oldfred said:**
> If the update grub does not find it, you have to add it to 40_custom and run the update grub.

[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
Yes, this solved it! Thanks heaps!

---


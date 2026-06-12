---
title: "New Hard drive - Grub2 will not boot - UUID invalid drops to busybox"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by JPWhite on 2010-11-13
I installed a new hard drive. Used Acronis True Image Home to clone old image to new HD.

Windows 7 boots OK. However Ubuntu will not boot. UUID of new HD is different.

I wiped the MBR and reinstaled grub2 from the LiveCD using CHROOT. Error still occurs.

How do I tell Linux the new UUID?

Boot error is /dev/disk/by-uuid/xxxx does not exist
dropping to shell

I can see new UUID of linux partition by running blkid and it not what the bootloader is expecting.

True Image resized the linux partition ading an extra 20GB, went from 500gb disk to 640gb disk.

Dual booting windows 7 and ubuntu 10.10

Any help to fix the UUID issue is well received :-)

Thanks

JP

---

### Post by JPWhite on 2010-11-13
Eventually found the fix myself.

All that is necessary is to press e in grub at bootup and manualy edit the UUID to be the correct one.

After Ubuntu comes up a simple

sudo update-grub 

does the trick.

I did run into a second problem with update-grub failing to register my windows 7 partition. It was due to a lower case /boot folder being in my system reserved partition. I renamed the lowercase /boot folder and reran update-grub and it found all boot images including win7. It is important to leave the uppercase /Boot folder alone on the system reserved partition, its windows boot.

The lower case /boot folder must have got there while I was trying to reinstall grub incorrectly during troubleshooting.

---


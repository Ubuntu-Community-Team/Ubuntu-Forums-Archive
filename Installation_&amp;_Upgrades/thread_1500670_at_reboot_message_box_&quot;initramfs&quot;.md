---
title: "at reboot message box &quot;initramfs&quot;"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by philo_71 on 2010-06-03
hi,
i have upgraded 8.04 to 9.10 by cdrom upgrade
>>mount -o loop /dev/cdrom /cdrom
>>umount /dev/cdrom /cdrom
./cdromupgrade--------------------------
------------------------------
process upgrade
-------------------------------
-------------------------------
---------- silo 32bit >> 64bit ---------------
silo -u -f 
reboot command doesn't work i reset hard !
----------------------------
the sytem boot, i think silo work's, but i have this message box "initramfs" 
can i do i have some command by help.
**********************************************************************************
booting with rescue 
-----------------------------------
mount ...........
mount...........
chroot 
----------------------------------
update-initramfs -u -k all
------------------------------------------
silo.conf
------------------------------------------
"ide=nodma" to kernel option
image=/vmlinuz
        label=Linux
        append="ide=nodma"
        initrd=/initrd.img
-------------------------------

again this message box "initramfs" 

Best regards
Philo

---


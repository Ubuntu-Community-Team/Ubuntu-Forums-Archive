---
title: "after ugrade grub problem"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by prokop1000 on 2013-10-26
Hello

I just upgraded my ubuntu and after the first restart its not booting up. Grub rescue console come up, with file not found error.
I have 2 hdds in raid with encryption
I tried to boot with live cd and run boot-repair, with the following results
```
[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will not act on the MBR.
The boot flag will be placed on mapper/nvidia_bbaeffhf1.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for **[/COLOR]fsck[COLOR=#666666])[/COLOR] except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
Disk /dev/mapper/nvidia_bbaeffhf1 doesn[COLOR=#BB4444]'t contain a valid partition table[/COLOR]
[COLOR=#BB4444]fdisk: unable to read /dev/mapper/nvidia_bbaeffhf2: Inappropriate ioctl for device[/COLOR]

[COLOR=#BB4444]fsck -fyM /dev/mapper/nvidia_bbaeffhf1[/COLOR]
[COLOR=#BB4444]fsck from util-linux 2.20.1[/COLOR]
[COLOR=#BB4444]Disk /dev/mapper/nvidia_bbaeffhf1 doesn'[/COLOR]t contain a valid partition table
fdisk: unable to [COLOR=#AA22FF]read[/COLOR] /dev/mapper/nvidia_bbaeffhf2: Inappropriate ioctl [COLOR=#AA22FF]**for **[/COLOR]device

fsck -fyM /dev/mapper/nvidia_bbaeffhf5
fsck from util-linux 2.20.1
fsck: fsck.crypto_LUKS: not found
fsck: error 2 [COLOR=#AA22FF]**while **[/COLOR]executing fsck.crypto_LUKS [COLOR=#AA22FF]**for**[/COLOR] /dev/mapper/nvidia_bbaeffhf5
mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]'crypto_LUKS'[/COLOR]
mount /dev/mapper/nvidia_bbaeffhf5 : Error code 32
mount -r /dev/mapper/nvidia_bbaeffhf5 /mnt/boot-sav/mapper/nvidia_bbaeffhf5
mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]'crypto_LUKS'[/COLOR]
mount -r /dev/mapper/nvidia_bbaeffhf5 : Error code 32
parted /dev/mapper/nvidia_bbaeffhf [COLOR=#AA22FF]set [/COLOR]1 boot on

                                                                          
Information: You may need to update /etc/fstab.

Disk /dev/mapper/nvidia_bbaeffhf1 doesn[COLOR=#BB4444]'t contain a valid partition table[/COLOR]
[COLOR=#BB4444]Disk /dev/mapper/nvidia_bbaeffhf5 doesn'[/COLOR]t contain a valid partition table

Boot successfully repaired.

You can now reboot your computer.
```

Could someone help me, how to solve this problem ?

thanks

---

### Post by oldfred on 2013-10-26
Boot-Repair is trying to run fsck as it cannot see encrypted partition and assumes it needs fsck. Can you mount and unencrypt it before running Boot-Repair or as part of running Boot-Repair?

Is grub2 & kernels in separate /boot partition outside RAID and encryption or inside it? 

I do not know RAID nor encryption, so cannot help much.

---


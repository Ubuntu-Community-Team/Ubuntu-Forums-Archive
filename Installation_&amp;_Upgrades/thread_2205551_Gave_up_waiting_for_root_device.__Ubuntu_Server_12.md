---
title: "Gave up waiting for root device.  Ubuntu Server 12.04 LTS"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by awclemen on 2014-02-14
When attempting to boot from new kernel (3.2.0-58) I get the following error message:

```
Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/HADRONE-root does not exist.  Dropping to a shell!
```

which drops me to the BusyBox V1.18.5 initramfs shell.

```
(initramfs) cat /proc/cmdline
root=/dev/mapper/HADRONE-root ro rootdelay=20 quiet splash
(intramfs) cat /proc/modules
radeon 738095 1 - Live 0xf85fe000
ttm 65344 1 radeon, Live 0xf843f000
drm_kms_helper 45466 1 radeon, Live 0xf84ae000
drm 197641 3 radeon, ttm,drm_kms_helper, Live 0xf84e2000
i2c_algo_bit 13199 1 radeon, Live 0xf8431000
video 19115 0 - Live 0xf8439000
floppy 60184 0 - Live 0xf846c000
e1000 101795 0 - Live 0xf8452000
megaraid_mbox 36082 1 - Live 0xf8427000
megaraid_mm 17891 1 megaraid_mbox, Live 0xf8411000

```

Now this happened after I upgraded and there was a dependency problem with initramfs - which I was able to straighten out, but I am stuck with this puppy.  I am however able to boot the the 2.6.32-48 kernel with no problem.  So I assume it has something to do with my boot setup.  I have reinstalled grub and then did a ```
update-grub
``` and have uninstalled and reinstalled the 3.2.0-58 kernel - but no fix.

```
(intramfs)blkid
/dev/sda1: UUID="43LKTc-017p-0DCR-lva0-TWtz-oul5-1uprKx" TYPE="LVM2_member"
/dev/sda5: UUID="d767ce76-b9ac-4bf1-8dfe-c1424cf6a26d" TYPE="ext2"
/dev/mapper/HADRONE-root: UUID="e64e02b8-e70b-4a08-9482-61e87e0145f8"  SEC_TYPE="ext2" TYPE="ext3"

```

I've tried swapping out /dev/sda5 for /dev/mapper/HADRONE-root and booting, but that didn't work.  I doubt that extending the rootdelay will fix anything as it works with one kernel.  Not sure why it can't find /dev/mapper/HADRONE-root... any ideas?

Thanks in advance.

---


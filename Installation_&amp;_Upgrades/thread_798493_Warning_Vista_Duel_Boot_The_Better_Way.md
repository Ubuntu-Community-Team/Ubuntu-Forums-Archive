---
title: "Warning Vista Duel Boot The Better Way"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by teaker1s on 2008-05-18
Many people are using grub to boot vista without a hitch so far. 
This is not the best way as:-
Vista sp1 will fail if grub is the boot loader

Encrypted drives and bitlocker issues

Any function relying on trusted  Platform Module will fail

the correct way is to chain load boot loaders vista boot loader if you select linux will load grub

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")



Also before trying to resize hd defrag and 
```
chkdsk /f
```

use ubuntu guided partitioning as gparted live iso corrupted ntfs file system and required knoppix fixntfs

---

### Post by SIXAXIS on 2008-05-18
I have Vista and Ubuntu and I use the GRUB bootloader. All you have to do to make Vista boot from that is run the Vista installation CD and click on the repair startup option. It allowed Vista to boot and surprisingly didn't erase the GRUB bootloader.

**EDIT:** Never mind.

---

### Post by Rallg on 2008-05-18
If anyone is worried about dual booting, there is also another way:

You can Make a USB pendrive bootable to DOS, and put GRUB4DOS there. There are some tricks (particularly, the USB will think it is hd0, and that your hard drive is hd1). When installing Ubuntu, do not install GRUB to the hard drive starting partition.

I won't give details here, because the procedure is described elsewhere. The advantage to dual-boot from USB is that your hard drive's MBR is not touched, and the Vista (or XP) bootloader is unaffected. Without the pendrive inserted and selected at boot time, Windows boots directly, without GRUB. So, there is no worry that a Windows update or re-install will confuse the boot.

The disadvtantage is that you can't boot to Ubuntu if your forgot to bring your USB pendrive. Of course, you can keep a copy of the necessary files. Also, the "automagic" GRUB update feature won't work, so if you re-format a partition (which changes its UUID) or update a kernel, you will have to manually edit the GRUB menu.lst on the USB pendrive.

I carry my laptop away from home, and don't have the Vista installation DVD with me. Since I boot to Ubuntu from USB pendrive, I don't have to worry about an update to Ubuntu doing something that would affect my boot.

---

### Post by logos34 on 2008-05-18
> **teaker1s said:**
> Many people are using grub to boot vista without a hitch so far. 
This is not the best way as:-
Vista sp1 will fail if grub is the boot loader

Encrypted drives and bitlocker issues

Any function relying on trusted  Platform Module will fail

In my experience Grub can boot Vista in most cases without a hitch.  Besides, most people do not have encryption.

> the correct way is to chain load boot loaders vista boot loader if you select linux will load grub

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")


This is well-known and already referred to in the user docs, among other places:
[https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28gracefully%29#head-e746e1f17e0fc71f1c95142f2558412cd6b3afe2](https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28gracefully%29#head-e746e1f17e0fc71f1c95142f2558412cd6b3afe2)

For those cases where Grub does not work with Vista I personally always recommend EasyBCD.

> Also before trying to resize hd defrag and 
```
chkdsk /f
```

use ubuntu guided partitioning as gparted live iso corrupted ntfs file system and required knoppix fixntfs

Yes, defrag (maybe two or three times) and chkdisk with error-correction.
But Gparted in general (whether the livecd or the version on the ubuntu install disc) seems to be the problem.  So the safest way is to resize Vista first using it's own built-in disk utility, then install linux.

---


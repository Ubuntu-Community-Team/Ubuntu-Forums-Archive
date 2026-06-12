---
title: "Big Error while trying to wipe partition"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Sun_Paladin on 2007-10-19
Okay. I tried to wipe the partition that contained my last install of Ubuntu(7.04). I'm pretty sure that I decided to wipe the partition that contained Ubuntu and not my Windows. I'm running on a laptop with Ubuntu and Windows XP dual booted. During the install of the OS, an error came up because the Live CD was corrupted a little bit from burning. When I tried to reboot again without the CD, I couldn't boot into Windows to get the image to burn a CD again. All I get is an error:

GRUB Loading stage1.5


GRUB loading, please wait...
Error15

Help would be greatly appreciated. Thanks.

---

### Post by tech9 on 2007-10-19
> **Sun_Paladin said:**
> Okay. I tried to wipe the partition that contained my last install of Ubuntu(7.04). I'm pretty sure that I decided to wipe the partition that contained Ubuntu and not my Windows. I'm running on a laptop with Ubuntu and Windows XP dual booted. During the install of the OS, an error came up because the Live CD was corrupted a little bit from burning. When I tried to reboot again without the CD, I couldn't boot into Windows to get the image to burn a CD again. All I get is an error:

GRUB Loading stage1.5


GRUB loading, please wait...
Error15

Help would be greatly appreciated. Thanks.

try burning another liveCD, but maybe 7.10 this time
Backup your data
Format the partition and install 7.10 clean

---

### Post by Sun_Paladin on 2007-10-19
Unfortuanetly, the 7.10 image is inside Windows which I can't get too. The computer doesn't even go into the dual boot screen. Was there a possibility that I wiped the XP partition instead of the Ubuntu partition? If I install the an uncorrupted CD of Ubuntu 7.10, then do you think I will gain access to my Windows side again?

Thanks.

---

### Post by LDRoamer on 2007-10-19
I had this problem. You need to boot your windows cd and go into the recovery console. This link describes the process:

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

If you google around or search the forums here you will find lots of help on this subject.

---

### Post by tech9 on 2007-10-22
> **Sun_Paladin said:**
> Unfortuanetly, the 7.10 image is inside Windows which I can't get too. The computer doesn't even go into the dual boot screen. Was there a possibility that I wiped the XP partition instead of the Ubuntu partition? If I install the an uncorrupted CD of Ubuntu 7.10, then do you think I will gain access to my Windows side again?

Thanks.

yes... just don't manually format your windows partition on install

---


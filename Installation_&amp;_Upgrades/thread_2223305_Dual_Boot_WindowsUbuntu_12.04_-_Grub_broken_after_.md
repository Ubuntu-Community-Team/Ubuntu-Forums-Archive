---
title: "Dual Boot Windows/Ubuntu 12.04 - Grub broken after upgrade to 14.04"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by liviusbr on 2014-05-10
Hi All,


Just wondering if any of you got into the following issue :

Dual Boot: Windows 7 Home Premium + Ubuntu 12.04
Bootloader : Grub

Life was good until I decided to upgrade to 14.04 via Ubuntu's CLI upgrade tool.
After reboot, I was not able anymore to boot into either Win or Ubuntu, stuck at grub rescue.

Tried a Win 7 boot disk, but I cannot either repair or install Windows on any partition. - UEFI ?
Tried Ubuntu Live CD (14.04) boot-repair tool, but did not help either. Boot seems to get stuck at "Lenovo" Splash scree. 
My laptop is a V-570 Lenovo.


Any idea?


Thanks,
Liviu

---

### Post by Devan_Phillis on 2014-05-10
if you have another computer available you could always use PLOP Boot Manager to control your boot. Couldnt hurt to give it a try.

[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

let me know how it goes

KD8MST

---

### Post by oldfred on 2014-05-10
You should be able to boot Ubuntu 14.04 from flash drive. And you can install Boot-Repair into that.
System is new enough that plop should not be required.

Some newer systems with Windows 7 but newer Intel i-series chips were UEFI/BIOS with Windows installed in BIOS mode. You then need to be sure to boot in BIOS mode if given two options to boot from BIOS.

Are you using a 64 bit install?

If getting grub rescue you may be able to manually boot. Or you may be able to boot with SuperGrub.

       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)


 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by Devan_Phillis on 2014-05-10
ok i like his fix better haha

---


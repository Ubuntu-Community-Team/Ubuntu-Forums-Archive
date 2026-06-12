---
title: "How to tell it not to overwrite MBR"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by beausimon on 2006-06-27
Hi,
I just downloaded ubuntu 6.06 liveCD. I want to dual boot with my existing win2k but do not want it to overwrite win2k's MBR because I'm planning to use a grub floppy for boot up.  Unfortunately, the liveCD installer doesn't provide an option not to overwrite the MBR. I intend to repair my win2k MBR and re-install ubuntu again. Is there any way to tell the ubuntu installer not to overwrite the MBR but to install its bootloader into its own partition?

Thanks.

---

### Post by confused57 on 2006-06-27
The Dapper 6.06-alternate CD gives you the option of where to install grub, either the mbr or to a floppy.  I don't think you can specify with the LiveCD, think it automatically installs grub to the mbr.
Are you planning on dualbooting with one hd, a different partition for Ubuntu; or are you installing Ubuntu to a second hd?

---

### Post by beausimon on 2006-06-27
[QUOTE=confused57]The Dapper 6.06-alternate CD gives you the option of where to install grub, either the mbr or to a floppy.  I don't think you can specify with the LiveCD, think it automatically installs grub to the mbr.
Are you planning on dualbooting with one hd, a different partition for Ubuntu; or are you installing Ubuntu to a second hd?[/QUOTE]

Hi,
I'm planning to install on a single HD but into a different partition. In my case, I've actually prepared 4 partitions (hda1 to hda4) with the intention to make hda2 partition just solely for grub. I'm trying to implement a multiboot method described by Saikee in the justlinux forum, which leaves the MBR untouched.

hda1=Win2k
hda2=small partition just for grub
hda3=Ubuntu "/"
hda4=swap

Do you think if I copy /dev/hda3/boot/grub to /dev/hda2/boot/grub and then repair the MBR, it would boot the grub in /dev/hda2 ?  If this works, then I won't have to download the alternate-CD and reinstall.

---


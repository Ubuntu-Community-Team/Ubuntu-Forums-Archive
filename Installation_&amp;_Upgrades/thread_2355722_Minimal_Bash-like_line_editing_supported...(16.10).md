---
title: "Minimal Bash-like line editing supported...(16.10)"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by schitza on 2017-03-15
I get this message after boot-repair fix with live usb.  [http://paste2.org/NAxGyFYY](http://paste2.org/NAxGyFYY)

Please help.

Thanks

---

### Post by TheFu on 2017-03-15
Use a liveBoot (flash drive?), go into recovery mode, open a root shell with /dev/sda1 as the mounted "/".
Run **grub-install /dev/sda** - /dev/sda is where you want it, if the drive order hasn't changed.
Run **update-grub**. The defaults should be fine. It should regenerate the needed config and install it correctly.

None of this will work if the system is configured for UEFI booting. The sda HDD is NOT currently setup for UEFI.
None of this will work if the disk order changes. 

If grub-install fails, DO NOT go further.
If everything goes well, exit, exit, exit until you can choose to reboot.  Then remove the flash drive before/while the BIOS screen is shown. After the screen flickers during a reboot is when I pull it.

If this doesn't work, recapture new, fresh, boot-info using the boot-info script (like you did last time) and post the new link.

---

### Post by schitza on 2017-03-16
Hy, thanks for the reply.
Currently my laptop screen is broken and i am using secondary display(tv).
When i press shift to enter recovery i loose signal on tv.
Is there any way around this?
Thanks

---


---
title: "Busybox and related errors including &quot;missing&quot; fixed disk"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-09-21
I just went through several days of Ubuntu "hell".  After I had a change in plans, I put back a motherboard I had taken out because of unfixable nVidia problems on the upgrade from 12.04 to 14.04.  I put in another fixed disk that was 12.04, and got this series of errors including cannot find the fixed disk, sbin/modprobe errors, all dropping me into busybox.  I did several tests with other fixed disks IDE, SATA, SATA SSD, reset the BIOS on the motherboard, and still had the errors.  I did  a clean install of 12.04 32-bit on an old 30 GB IDE HDD.  Still the had the same problem.  I tried several of the fixes found on this forum.  Still no luck.  I knew the motherboard was likely good, as fixed disks with a Win XP partition would boot without a problem.

I then cut a 32-bit boot repair disk and started looking at the grub options including the root delay 90 one.  I took a chance, added the root delay 90 and won.  All the boot errors went away.

Is there any reason why this worked?

John

---


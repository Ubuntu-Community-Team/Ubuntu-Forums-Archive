---
title: "can't install ubuntu - cpu problem?"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by bradlewa on 2011-04-16
Hi, I've been trying to install Ubuntu (any variant, 10.04, 10.10, 11.04 - either i386 or x64) on my desktop computer that already has Win7 installed.  I've used Ubuntu before, I've dual-booted on other systems before, so I'm not sure what the issue is right now.

I've cleared 40 GB of space on my hard drive, and then try to boot from the LiveCD (checked the MD5 Sum, and it's fine).  I can get to the initial boot screen where it says Ubuntu, and there are the 4 or 5 small dots underneath changing color, but then the screen will go to black with white text.  I've copied some of it, but it's at this point the system will reboot, so it's tough to get all the info copied.

Here are some of the lines I've seen:

No human readable MCE decoding support on this CPU type
Processor context corrupt
Kernel panic
Fatal machine check on current CPU
Some CPUs didn't answer in synchronization

I'm running a Core i7 720 on an EVGA X58 motherboard with 12 GB 1066 RAM.  I have an EVGA nVidia 285 installed.

I had read some threads about using the nomodeset option when booting from the LiveCD, but this didn't help at all.

I'm wondering if anyone knows what the problem is, and where I could begin trying to troubleshoot.  I did searches for some of the lines I typed above, but didn't really get anything that fit my situation.

Thanks in advance!

---

### Post by Dutch70 on 2011-04-16
Try some of these boot options, especially nomodeset, but the others may be needed with your gpu.
[[COLOR="Red"]How to set NOMODESET and other kernel boot options in grub2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="Red"]https://help.ubuntu.com/community/LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by bradlewa on 2011-04-16
Thanks for the response, but nomodeset doesn't work for me.  I tried all the options available under F6, and none of them work unfortunately.

---


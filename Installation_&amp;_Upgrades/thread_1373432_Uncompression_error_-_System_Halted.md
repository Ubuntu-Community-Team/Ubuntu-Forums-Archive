---
title: "Uncompression error - System Halted"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by Tovam on 2010-01-05
I wanted to install Ubuntu 9.10, so I downloaded it and burned it on a cd. When I rebooted my pc, I got to the familiar liveboot screen, and and I selected to run Ubuntu from the cd. That made everything freeze, so I had to reboot.
This time, I choose to check the cd for errors. It took quite a while in which it didn't seem to do anything, then it gave me a black screen full of lines like...

2.268065] [<c01501f6>] ? run_time_softirq+0x156/0x200
2.268118] [<c0128ca2>] bad_area_nosemaphore+0x12/0x20

Anyway, I figured the iso was somehow corrupt, so I downloaded it anew. The SHA256SUMS was correct, but it gave exactly the same problems.

I tried booting from usb too, but that didn't work. Trying the cd on another pc to see if it works there is not an option at the moment.

Does anyone know what I can do to fix this, or how else to install Ubuntu 9.10 (install, not upgrade).

Thanks in advance.

---

### Post by tachuela on 2010-01-05
Try other disks that you know have booted before or try SystemRescueCD:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by raymondh on 2010-01-05
or you can try the alternate CD/install which is text based instead of GUI-based hence uses/requires less resources to install.

Regards,

---

### Post by Tovam on 2010-01-06
Neither the SystemRescueCD nor Ubuntu 9.10 Alternate want to even boot. 9.04 does want to boot, but there's a problem with installing (and I want 9.10 in the end anyway).
Could this be because of incompatible hardware? A corrupt iso (the SHA256SUMS were all correct though)? Something wrong with the burning or reading of the cd (looking for other pc to test this on)? Or something else?

---

### Post by pjrodz on 2010-05-22
try installing using another usb flash disk

---

### Post by inbox on 2010-07-23
Hi,

I'm french. So don't panic about my english.

Y encoutered this problem of "Uncompression error -- System Halted". In my case, this was RAM problem. You can verify this by launching a Memtest86 with a live CD.

---


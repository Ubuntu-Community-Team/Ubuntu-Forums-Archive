---
title: "Unable to complete install"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by lt paul on 2006-06-18
I've been struggling with my 6.06 install all day. I downloaded the ISO's but due to some problems involving a Drive appears confused (ireason = 0x02) error could not complete installation. I tried the instructions for a network install by booting the kernel and initrd.gz image files of my windows partition using grub for ntldr, which went fine until the first reboot, where it gets all the way to starting the kernel logs before switching to a console screen with a blinking cursor, after a few seconds the  cursor stops blinking and I can't get any response. Booting into recovery mode and examining the logs revelealed it was having the same drive is confused problem just before the freeze. Unplugged both CDROMS and rebooted, same problem, last kern.log entry is APM:bios not found. At this point I don't know what too do. Machine is an old compaq with a 900Mhz Athlon tbird on a Via chipset.

---

### Post by lt paul on 2006-06-18
Solved the lockup issue. It seems that there were some serious configutation issues with my X. I removed my secondary videocard and x was able to tell me that it was having problems. Reconfigured X and was able to get it running. I'm now having some issues with the Nvidia driver but I will post that elsewhere.

---


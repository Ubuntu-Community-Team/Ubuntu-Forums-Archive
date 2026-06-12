---
title: "upgraded GRUB to XX-15, can I remove xx-14?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by whitehaint on 2009-11-23
Well after doing a nice number on my installs I reformatted and installed and went to ext4 for fun.  While it was running the updates it came across a slightly newer version of the GRUB and it asked what to do and I obviously said update it.  It did, I rebooted and now I have to versions of 9.10 on my boot options (along with XP).  I wanted to know if I can remove that older version, and if so how as they are on the same partition.

---

### Post by phillw on 2009-11-23
> **whitehaint said:**
> Well after doing a nice number on my installs I reformatted and installed and went to ext4 for fun.  While it was running the updates it came across a slightly newer version of the GRUB and it asked what to do and I obviously said update it.  It did, I rebooted and now I have to versions of 9.10 on my boot options (along with XP).  I wanted to know if I can remove that older version, and if so how as they are on the same partition.


You'd be best advised to tag a question to drs305  for that.  At the moment he's here there and everywhere for Grub stuff. You can track him down by his Sig ..

It appears in this thread [http://ubuntuforums.org/showthread.php?p=8351675](http://ubuntuforums.org/showthread.php?p=8351675)

He's a real nice guy and answers questions - It's just a case of finding the best thread for you !!!

Last seen over here --->  [http://ubuntuforums.org/showthread.php?t=1287602&page=4](http://ubuntuforums.org/showthread.php?t=1287602&page=4)

Regards,

Phill.

---

### Post by falconindy on 2009-11-23
I think you got a new kernel, not a new version of GRUB. Karmic still runs on Grub 1.97 beta4. Easiest way to remove the old kernel (which should be safe provided your new kernel isn't giving you any problems) is to open up Synaptic and search for "linux-image". Be **very** careful to make sure the only thing you remove has the -14 suffix on it.

---

### Post by whitehaint on 2009-11-24
I stand corrected, it is the kernel.  I'll give that a shot and see what happens.

---

### Post by drs305 on 2009-11-24
If you aren't sure how to remove kernels, there is a section in the SUM link below (StartUp-Manager) that explains the various ways to do it. Although SUM doesn't remove kernels, and has mixed results with G2 in any case, the section on removing kernels still applies.

---

### Post by dhavalbbhatt on 2009-11-24
If I can give you some advice - don't remove xx-14 kernal right now. I don't believe xx-15 is the latest stable version, I believe it is still beta/rc version(?) There are many applications out there that still rely on having xx-14 kernal version and are not compatible with xx-15, those programs may ask you to re-install xx-14. Having said that, if you just want to change the current the grub menu to not reflect two kernal options during boot up, then ask your question with that in mind. I am not an expert in grub 2, so can't help you there.

---

### Post by phillw on 2009-11-24
> **dhavalbbhatt said:**
> If I can give you some advice - don't remove xx-14 kernal right now. I don't believe xx-15 is the latest stable version, I believe it is still beta/rc version(?) There are many applications out there that still rely on having xx-14 kernal version and are not compatible with xx-15, those programs may ask you to re-install xx-14. Having said that, if you just want to change the current the grub menu to not reflect two kernal options during boot up, then ask your question with that in mind. I am not an expert in grub 2, so can't help you there.

+1 on keeping 14, people are reporting issues with 15. It's always a GOOD idea to keep the previous, known working, version of a kernel in case you need to boot into it. They don't take up much room.

Phill.

---


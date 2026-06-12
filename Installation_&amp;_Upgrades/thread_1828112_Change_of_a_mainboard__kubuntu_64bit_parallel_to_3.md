---
title: "Change of a mainboard / kubuntu 64bit parallel to 32bit"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by ritchie-w on 2011-08-18
Hello,

If I change the mainboard of a kubunto 11.04 (32bit) installation,
Do i have to reinstall the system or does the actual kernel can handle the change of a mainboard (core2 -> icore 7).

Can I install a 64bit kUbuntu as a additional OS, so that i will have 

- windows XP
- kubuntu 11.04 (32bit)
- kubuntu 11.04 (64bit)

Can grup and linux itself handle this. I would like to speed for the 64Bit kubuntu a seperate hard disk. Is there somewhere a description for such a configuration.

Thanks for help

R.

---

### Post by oldfred on 2011-08-19
The issue will be more Video and perhaps some other drivers. I updated a new motherboard and new video card and it just rebooted. But my processor was the same & I went from nVidia 7600 to 9600gt.

As I understand it there are issues with the new built in video in the newer Intel chips and it may even depend on which version of chip you have.

You also may have issues with BIOS/UEFI and MBR(msdos) and gpt. The new motherboards have a BIOS mode so it should work, but they also have the new UEFI mode which is more the future.

---


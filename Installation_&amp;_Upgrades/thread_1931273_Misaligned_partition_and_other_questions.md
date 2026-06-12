---
title: "Misaligned partition and other questions"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by thedarkorb on 2012-02-25
I've been casually using Ubuntu for a few years but this is the first  time I've had real trouble installing the OS. I bought a Lenovo laptop and I've run into a few problems after installing:

1. After formatting the drive and installing Ubuntu 11.10 (64 bit) the  disk utility gives me the message "the partition is misaligned by 3072  bytes" and suggests repartitioning. I formatted and reinstalled and am  getting the same message. How exactly do I align a partition properly?

2. The laptop in question has 4 gigs of RAM but Ubuntu seems to only  detect 3.5. Why is this and what can I do to make sure the system uses  all four gigs?

3.When shutting down the laptop hangs at the Ubuntu screen. The only way to turn it off is to hold down the power button.

Also, I've read that 64 bit Ubuntu has issues with flash. Is this still the  case? Am I better off installing the 32 bit version of 11.10? Any help with these issues would be much appreciated as I'm in over my head here.

---

### Post by darkod on 2012-02-25
2. Most laptops use integrated graphics. Usually in BIOS there would be a setting how much memory from the RAM to dedicate to the graphics. This memory is chopped of on BIOS level and the OS doesn't even see it as existing. If it is set at 512MB for example, 3.5GB from 4GB sounds right.

64bit ubuntu has no problem with flash. Personally I just copy one .so library to the firefox plugins folder and it works, but there is also a dedicated installer which should install 64-bit flash properly. In any case, you can make it work easy.

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for newer installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

---


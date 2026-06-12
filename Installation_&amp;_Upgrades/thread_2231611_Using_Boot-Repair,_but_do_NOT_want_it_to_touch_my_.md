---
title: "Using Boot-Repair, but do NOT want it to touch my Windows Bootloader? HOW?"
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by SkOrPn on 2014-06-26
I have Windows installed and running on RAID0, working brilliantly and perfectly, would take a nuclear bomb to break it. However, I have Ubuntu on a completely different hard drive and on a completely different SATA controller in AHCI mode. I use the BIOS to select what controller I want to boot. WHY? because I am tired of Linux destroying my working Windows/Business setup. I am tired of Ubuntu breaking, I am tired or having to reinstall everything because Grub wants to break when you breath on it. This way I can do what ever I want to my Linux drive and it will NOT affect the way my Windows and employers software functions. It will just boot and just works.

Now to my problem. I was in my Ubuntu 14.04 installation when it informed me of a measly 85 mb of updates, so I installed them and when it rebooted I get nothing but a black screen. I tried using recovery but when I hit the "SHIFT" key I get

```
Environment Block
 Press any key to continue...
```
When I hit a key to continue I get nothing what so ever. Black screen forever...

Now, I am in the Live USB session trying to fix it and I just finished installing Boot-Repair when it occured to me maybe I better not use this because it may, not only not work, but also break my Windows bootloader (and that would anger me to no end)? Can I use Boot-Repair and go into the advanced settings and tell it to NOT look for other OS's, and NOT to mess with my Windows Bootloader on the RAID0 array PLEASE? If so, what settings should I use in Boot-Repair to make it ignore the Windows partition? Or should I just take my case apart again and disconnect the Windows SATA cables to make sure Ubuntu does not break it yet again?

Thank you for any help please.

---

### Post by oldfred on 2014-06-26
Yes, advance settings should work. Or just do everything manually which is what Boot-Repair has automated.

DO NOT run the auto fix as with multiple drives it will install grub to the MBR of every drive. With RAID you should not be using MBR, but root of RAID to boot but best not to tempt fate.

But if you can get to grub menu, or holding shift key if BIOS, from BIOS until menu appears, Boot-Repair will not help much. It fixes grub issues, not configuration after you select a boot with grub.

Did you install a different video driver? sor some other major system configuration change?

From recovery mode you should get to a menu where you can continue to boot, or go to a terminal mode with or without Internet to run commands to fix system.

---


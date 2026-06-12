---
title: "Added third OS and can only see two"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2009-11-29
Acer laptop updated to karmic, was dual boot with Win 7RC.  Added XP on a third partition and can only boot into Karmic or the new XP (Grub says Win 7 but boots XP).  7 is still there but it is beyond my knowledge to change menu.lst to point to 7.  Any help appreciated.

---

### Post by sakisds on 2009-11-29
Windows XP does not recognize Windows 7 on installation, so its not preparing the bootloader to use windows 7 too. I think if you boot with the Windows 7 installation disk and run startup repair, it will overwrite grub with a win7/winxp bootloader. Then you can reinstall grub and everything will work fine(You will have one entry named windows, and then another menu to choose windows version).

Maybe you can add another menu.lst entry, same as windows 7 one, but changing the partition to use chainloader, but i am not sure.

---

### Post by lift_test on 2009-11-29
May try that but the win 7 is an RC not the release version and might not have recovery on the CD.  When I look at the HD with GParted it shows Karmic as sda 1, win 7 as sda 2, XP is sda 3 and obviously the swap is sda 4.  What I need to do is relate that to the grub entry. at the moment it looks like this

# This entry automatically added by the Debian installer for a non-Linux OS
# on /dev/sda2
title          Windows 7 RC (loader)
rootnoverify   (hdo,1)
saved default
makeactive
chainloader     +1

Although it says sda 2 correctly it actually loads XP.  If I change the hd0,1 to hd0,0 and add another entry to XP using hd0,1 would that give the desired result?

It may seem a strange thing to do but I like using both 7 and Karmic but there is a Win program that cannot be run under Karmic which requires a very specific driver.  I have found that if another driver is loaded first the one I want will not be loaded and 7 can't be persuaded to change it.  Hence an new XP purely to run one program with a specific driver.

---

### Post by darkod on 2009-11-29
You can try adding the entry manually, that's the first option. However it might not work because windows seems to combine somehow the boot process for all versions of it. I don't have much experience because I never had two ver of win at the same time.
The chainloader +1 command is just chainloading (continuing) with the windows bootloader however if the process is not complete (looking at windows only), it might not work because of that.
Try adding the entry first, and change the title of the current entry because it boots XP not 7. After that the suggestion to repair windows MBR is the correct one. That should create windows bootloader with both 7 and XP and after that reinstalling grub1 will add that combined bootloader into menu.lst.
Even if it was RC win7 dvd should have the Repair This Computer option at start (after the language selection screen).

---

### Post by lift_test on 2009-11-29
> **darkod said:**
> You can try adding the entry manually, that's the first option. However it might not work because windows seems to combine somehow the boot process for all versions of it. I don't have much experience because I never had two ver of win at the same time.
The chainloader +1 command is just chainloading (continuing) with the windows bootloader however if the process is not complete (looking at windows only), it might not work because of that.
Try adding the entry first, and change the title of the current entry because it boots XP not 7. After that the suggestion to repair windows MBR is the correct one. That should create windows bootloader with both 7 and XP and after that reinstalling grub1 will add that combined bootloader into menu.lst.
Even if it was RC win7 dvd should have the Repair This Computer option at start (after the language selection screen).

Tried that, Win 7 repair says it can't fix it.  Have also tried installing grub2 because it's supposed to automatically detect al OS's but it hangs every time I try to install.  Thank you for the encouragement.

---


---
title: "Error: File not found Grub rescue&gt;"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by aalapkbharucha on 2012-03-18
I was using ubuntu 11.10. Then also I wanted to add Windows 7. So I formatted the whole system, and installed win7 on single partition. Now I want to install Ubuntu 11.10 again. So I made Ubuntu11.10 USB installation and boot it. But as soon as I boot it,it is giving me following error:
error:file not found
grub rescue>

What should I do? Kindly help me.!

---

### Post by aalapkbharucha on 2012-03-19
Guys,kindly help me out here. I am searching google but not getting the answer..

---

### Post by efflandt on 2012-03-19
Whatever you did, it sounds like part of grub is still in the mbr of your hard drive, but you reformatted over its files, and apparently installing Windows did not install its own mbr (unusual).

So you are booting the stub of grub from the mbr of your hard drive, instead of booting from the USB device. A clue is that if you made the install iso on USB using "Startup Disk Creator" in Ubuntu, that bootable USB does not even use grub to boot itself.

Make sure that you are pressing whatever hotkey you need to press during BIOS splash screen to select boot device, and make sure you are booting the USB and not your internal hard drive (only until after you do the Ubuntu installation).

---

### Post by oldfred on 2012-03-19
+1 on efflandt suggestions.

Does Windows boot ok without USB flash drive, if not did it fully install or do you have more than one hard drive? Windows boot loader may have installed to the other drive.

If Windows boots you should use Windows to shrink the Windows partition and reboot several times as it will run chkdsk and make some repairs for the resize.

---


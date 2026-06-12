---
title: "Fresh install of windows 7 not working with Ubuntu"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by pimaster on 2013-03-31
Hello, I recently started using Ubuntu on a dual boot with windows 7 however after re-installing windows 7 on the same partition as the old version of w7, I no longer boot to the Ubuntu boot options menu, meaning that it boots straight to windows. Sorry as I am a bit new to dual booting!
Any help would be greatly appreciated!

---

### Post by Jay_E on 2013-03-31
windows does not play well with others.
when you install/recover windows, it grabs the *whole* disk.

that erased ubuntu.

to verify, get gparted-live (or a liveubuntu) on a usb. boot that. run gparted and see.
try not to get too discouraged.
 have fun,
jay

---

### Post by pimaster on 2013-03-31
Thanks, but I am pretty sure that it hasn't deleted ubuntu as in disk management it  says I have the two partitions ubuntu (I don't know why it has two but they both run the same ubuntu).. Can I begin an ubuntu installlation then stop just before it begins deleting files and see if the ubuntu boot selection returns? Any ideas, I don't mind re-installing ubuntu but I would prefer not to.

---

### Post by pimaster on 2013-03-31
Wait sorry it has deleted them... it says they are both 100% free I will begin the re-installation now, thanks!
Jonny

---

### Post by oldfred on 2013-03-31
If you looked from Windows it will show them as free, but if you specifically installed Windows to the same partition it should not have overwritten the Linux partitions. Windows does not "see" Linux partitions.
IF you looked from LiveCD/DVD/Flash and they are gone then you installed Windows to the entire drive. That most often occurs with the use of the Vendor's Recovery Windows reinstall as that restores system to as purchased.

It may just have installed its boot loader over the grub boot loader in the MBR.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by pimaster on 2013-03-31
Thanks, but I deleted the ubuntu partition before I  read this... anyway I wanted a fresh start. Just looking up how to shrink a windows partition to over 50% of the total hdd capacity. Thanks all for the help!

---


---
title: "How large can the latest version wubi install up to?"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Burky on 2009-11-19
For example I ordered a computer with 1tb harddrive, will be able to install Ubuntu with a 500gb partition? Or would I have to do that myself?

---

### Post by darkod on 2009-11-19
I'm sure there are conflicting opinions but in my personal humble opinion wubi is just an easy way for long time windows users to test it installing it like any windows app.
If you are decided to have Ubuntu as single or dual boot, I see no reason to bother with wubi. It can only make complications for you. And if you want to check out Ubuntu first, again wubi is not needed, that is why you can boot with the CD and select the first option, Try Ubuntu without changes to the computer.

---

### Post by Burky on 2009-11-19
But how hard is it to uninstall a dual boot?

---

### Post by darkod on 2009-11-19
You mean a proper dual boot, right? Not wubi?
There is no  need to uninstall anything. For example, you decide tomorrow that you don't want to use ubuntu any more. Just open either gparted from livecd or windows disk management, delete ubuntu partitions, create ntfs partitions and use that space in windows.
In some situation you could even continue booting windows with grub, especially if it was and remained on the first partition. No need to even restore the windows MBR, but it is recommended in situation like that. And the process is not difficult at all.

PS. I stand corrected, you can't continue booting with grub, /boot/grub will be gone. :) But the rest is still true, I swear. :)

---

### Post by wojox on 2009-11-19
Just delete the partition and reconfigure the mbr.

---


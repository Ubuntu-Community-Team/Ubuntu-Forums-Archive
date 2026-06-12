---
title: "Dual boot pre-encrypted Windows and Ubuntu?"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by screennameless on 2010-03-14
So I have this encrypted Windows partition. I used Truecrypt. Now, I'm trying to install Ubuntu as a dual boot next to Windows. Unfortunately, I can't seem to find a way to resize the encrypted Windows partition OR install GRUB without wiping out the Truecrypt bootloader.

Is there any way I can do this without decrypting Windows and then performing the actions, then reencrypting Windows?

Any help is greatly appreciated.

---

### Post by Mark Phelps on 2010-03-14
I'm presuming you encrypted the whole MS Windows partition, not just some files ...

That being the case, there is no way to resize the encrypted partition without first, booting into it.  This, of course, requires knowing the encryption access and password info.

If you're running Vista or Win7, you can use the Disk Management utility to shrink the partition.  Would first make a backup of your important data, though.

---


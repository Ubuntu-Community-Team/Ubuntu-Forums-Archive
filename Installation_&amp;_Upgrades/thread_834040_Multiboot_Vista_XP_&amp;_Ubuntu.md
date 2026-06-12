---
title: "Multiboot Vista XP &amp; Ubuntu"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by sbooder on 2008-06-19
Hi all,
                I been registered here for a while but only just got round to finding time to multiboot Ubuntu on to my new PC.
I have a Dell Inspiron 530, 2GHz Dual Core 2GB RAM and a 300GB HD.  I have already set up a Vista, XP dual boot using this tutorial ([http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html](http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html).

I now want to add Ubuntu to the fray, and wondered if following the steps in this thread ([http://ubuntuforums.org/showthread.php?t=260772](http://ubuntuforums.org/showthread.php?t=260772)) would be a wise move or not, with the following being the last step I took setting up the dual boot Vista XP:

bcdedit –set {ntldr} device partition=C:
bcdedit –set {ntldr} path \ntldr
bcdedit –displayorder {ntldr} –addlast 
bcdedit -set {ntldr} description "Microsoft Windows XP"

Also can I load XOSL in vista on NTFS or is it always preferable to shrink the Vista drive to create a separate FAT32 drive for XOSL?

Or Can I use Wubi with an existing Vista XP dual boot?

Thanks for any help.
Simon.

---

### Post by Sef on 2008-06-19
> Also can I load XOSL in vista on NTFS or is it always preferable to shrink the Vista drive to create a separate FAT32 drive for XOSL?

NTFS is preferable to FAT32.  NTFS-3g can be downloaded and allows you to read and write to NTFS from GNU/Linux.


> Or Can I use Wubi with an existing Vista XP dual boot?

Yes, that is another option.

---


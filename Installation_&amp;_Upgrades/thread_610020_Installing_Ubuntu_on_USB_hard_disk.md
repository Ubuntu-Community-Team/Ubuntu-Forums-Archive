---
title: "Installing Ubuntu on USB hard disk"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by shahein on 2007-11-11
Hello,

I am trying to install Ubuntu on an external USB hard disk, I tried different ways from different internet sites, none of them working until now. I would appreciate it very much if some one can help me to answer those few questions which might be helpful for me. I already installed on the USB H.D. but after restart, nothing is happen, no Grub, nothing at all, it just loads the Windows.

Is it necessary to install the Grub on the (hd0) or I can install over the (hd1) which is the USB H.D.?

What does it mean virtual swap and where to modify it? "http://www.dedoimedo.com/computers/grub.html#mozTocId288068"

What is the source of this error message?
"Grub loading ...
Error 21"

Is LILO more efficient than Grub in this matter?

IS it must to umount the USB H.D. before installing Ubuntu on it?

Does any one knows a useful link that might help me?

Thanks in advance.

Best regards.

Ahmed Shahein.

---

### Post by logos34 on 2007-11-11
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(-->post #502)

maybe your problem was that you didn't edit menu.lst from (hd1,x) to (hd0,x).  Change and [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351") to mbr of usb

Grub is better than lilo

yes, the partition you are installing on must be unmounted

---


---
title: "Deleted partition table; UEFI/BIOS install issues"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by Julio_Rossoni on 2015-11-12
Hi. I started testing Ubuntu Gnome on Live (Try out) today, approved it, and I`ve decided to install it. So, I messed it up. I accidentally (or noob-ly) deleted every partition table (problem identical to this one, i guess, though It didn`t work for me [http://ubuntuforums.org/showthread.php?t=2000824](http://ubuntuforums.org/showthread.php?t=2000824)), and now I can`t boot the computer nor on Ubuntu or Windows. I just can`t. I need your help. I might have misunderstood some information, and I switched BIOS to Legacy and UEFI. Then I started rebooting (since I couldn`t start windows our ubuntu), and now I have no idea in which it should be.

---

### Post by oldos2er on 2015-11-12
Moved to Installation & Upgrades; given a meaningful title.

---

### Post by grahammechanical on 2015-11-12
If we delete partitions we loose all the data on those partitions. And that includes operating systems. Is there data on the hard disk that you cannot afford to lose? Do you wish advice on how to recover data from a deleted partition? If you try to install Ubuntu you may over-write parts of the hard drive which contain data you wish to recover and that will make it impossible to recover the data.

If all you want to do now is install Ubuntu then you can install Ubuntu in EFI mode or BIOS/Legacy mode. It does not matter which. If you wish to install Windows 8 or Windows 10 then you should install Windows in EFI mode and then install Ubuntu in EFI mode also.

Regards.

---

### Post by oldfred on 2015-11-13
Is drive totally blank, or do you have partitions?

Post this from terminal in live installer:
sudo parted -l

---


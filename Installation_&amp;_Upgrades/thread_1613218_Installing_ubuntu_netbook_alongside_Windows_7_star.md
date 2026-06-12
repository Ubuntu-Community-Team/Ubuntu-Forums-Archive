---
title: "Installing ubuntu netbook alongside Windows 7 starter"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by yesar92 on 2010-11-04
Hello all,

I have downloaded the ubuntu netbook edition for my dell inspiron 1012 mini notebook and I want to install it alongside with Windows 7 starter edition like what I have on my desktop computer , and choose from the OS boot menu the os I want to operate , is that possible? knowing that I have one drive only , and the minibook is not partitioned. 

Thanks!

---

### Post by Fafler on 2010-11-04
Yes. The installer handles all that, resizing your current partition and installing the bootloader. Just pop the CD in, boot into the installer and follow the instructions.

---

### Post by Quackers on 2010-11-04
It is safer to resize your Windows partition from within Windows, and much quicker.
Go to Start and right-click on Computer then select Manage. In the window that appears click Disk Management. When a graphic of your hard drive appears right-click on the Windows drive and select Shrink. It will tell you how much shrinkage is available - usually about half. Click ok and 30 seconds later it's done. The resulting unallocated space can be used for side by side installation of Ubuntu.

---

### Post by yesar92 on 2010-11-05
> **Quackers said:**
> It is safer to resize your Windows partition from within Windows, and much quicker.
Go to Start and right-click on Computer then select Manage. In the window that appears click Disk Management. When a graphic of your hard drive appears right-click on the Windows drive and select Shrink. It will tell you how much shrinkage is available - usually about half. Click ok and 30 seconds later it's done. The resulting unallocated space can be used for side by side installation of Ubuntu.

I am shrinking the volume right now , lets hope this works , Windows 7 starter is so stupid version of windows.  

What happens after shrinking? will a new partition appear?

---

### Post by Quackers on 2010-11-05
No, some unallocated space will appear. Ubuntu can then use this space to install itself.

---


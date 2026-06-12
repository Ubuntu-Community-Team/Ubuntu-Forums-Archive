---
title: "Install of Ubuntu Studio besides Windows11: resizing Windows partition ?"
date: 2022-06-17
forum: Installation &amp; Upgrades
---

### Post by vincentm77 on 2022-06-17
Hi everyone,

I have just bought a new laptop with Windows 11.
I would like to resize the Windows partition and install Ubuntu Studio (dual boot system).

Does the Ubuntu installer offer to resize the Windows partition ?!

Thanks
Vincent

---

### Post by yancek on 2022-06-17
The best thing to do in this case is to use the windows Disk Management tool to resize(shrink) the largest windows partition to create unallocated space then reboot windows to verify that it still boots and probably run chkdsk on it.  The windows C:\ partition is generally the largest.  Read through the link below which explains dual booting with windows.  Understand the difference between UEFI (which is likely what windows uses) and Legacy/CSM and if windows is UEFI, install Ubuntu UEFI.  You can find countless tutorial online so if the link below doesn't explain to your satisfaction, do an online search for dual booting window/Ubuntu.
If the windows OS is detected by the Ubuntu installer, it will give you the option to Install Alongside Windows.  If you don't see windows when you start the Ubuntu install, boot back into windows and turn off fastboot and hibernation. 
 
[URL="https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/"]https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/

[/URL]

---

### Post by ActionParsnip on 2022-06-18
I suggest you rise NTFS in Windows. It is a proprietary file system to Microsoft and only they know how it fully works. Once you yfree space you can use it to install Ubuntu

---


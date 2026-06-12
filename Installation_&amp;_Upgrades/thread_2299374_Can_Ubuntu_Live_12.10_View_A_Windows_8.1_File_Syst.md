---
title: "Can Ubuntu Live 12.10 View A Windows 8.1 File System ?"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by victor432 on 2015-10-17
OK what I want to know is can I boot from a Ubuntu Linux Live 12.10 DVD which will allow me  to examine the content of the hard drive without allowing the OS or ANY  third party software or driver to load ? Does Ubuntu Live 12.10 have a File System Explorer GUI utility (similar to Windows 8.1 File Explorer) which could allow me to navigate the Windows 8.1 file system by way of a mouse from the Ubuntu Live desktop ? The computer is a Windows 8.1 64bit laptop and the drive has Windows 8.1 installed on it.


  Help please

---

### Post by deadflowr on 2015-10-17
Sure, as long the Windows 8.1 system isn't encrypted, one would think.
Linux systems can read (and write) to ntfs file systems

From a live session of Ubuntu just click on the Files icon to open the file manager.
The file manager will have a side pane that should should a section called Devices.
Listed in Devices should be the partition(s) for Windows 8.1.
If you click on that(those), the Windows 8.1 partitions should mount and open for you to read.

---

### Post by victor432 on 2015-10-18
> **deadflowr said:**
> Sure, as long the Windows 8.1 system isn't encrypted, one would think.
Linux systems can read (and write) to ntfs file systems

From a live session of Ubuntu just click on the Files icon to open the file manager.
The file manager will have a side pane that should should a section called Devices.
Listed in Devices should be the partition(s) for Windows 8.1.
If you click on that(those), the Windows 8.1 partitions should mount and open for you to read.

Yes I don't believe the drive or the installation is encrypted. How can I check that is not encrypted ?

Thanks

---

### Post by Bucky Ball on 2015-10-18
Just a caveat to the instructions from deadflowr: Boot to Windows first, switch off hibernate, and then shut Windows down completely. If you don't do this Windows won't actually shut the drive/close the partitions and therefore you will not be able to access them from a Live session.

Another caveat: best to look but don't touch if you are tweaking with the actual Windows partition (where the OS is). If you start diddling with Win OS files from the Ubuntu side you can evoke some serious demons when you boot to Windows again. Just looking is fine, but don't start moving around or editing Win system files.

As outlined previously, boot from the Ubuntu install media> 'Try Ubuntu', you're at a desktop where you can look at what you want in a file manager (Nautilus).

Also throwing this in, but doesn't matter a lot as you're not installing Ubuntu: 12.10 is no longer supported. If you DO decide to install Ubuntu at any point, don't install 12.10. :)

---


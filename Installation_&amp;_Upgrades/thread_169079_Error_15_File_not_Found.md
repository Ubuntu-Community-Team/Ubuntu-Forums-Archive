---
title: "Error 15: File not Found"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by zackiv31 on 2006-05-01
root (hd0,1)
loads kernel
loads initrd
savedefault

Error 15: File Not found

Press any key to continue....

Any idea how I found out what file is not found?

I have a Raid0 system and the memtest 86 image loads from same boot directory so its not a problem with mapping...

---

### Post by Sef on 2006-05-15
This is what Linuxselfhelp says about error 15:

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Looks like it would be best to reinstall GRUB.

You can use the Ubuntu Live CD to reinstall GRUB.

---

### Post by julius.luo on 2006-11-04
I have same problem as you, and this was not only to my ubuntu but also Windows booting.

From the reply by Sef, it reminded me about my newly inserted hard disk. I did not product any operation of my another 80G disk, which is on WindowsXP, but I did find some odd behaviors of the performance of the linux system, and 15 error was always the message I met during system booting. 

After I have removed that hard disk, 15 error no more.

---

### Post by deagol666 on 2008-02-10
I have the same problem - how do i reinstall a grub without doing a full reinstall? Yes i'm a newb.

---

### Post by Partyboi2 on 2008-02-10
[Here]("http://ubuntuforums.org/showthread.php?t=224351") is how to restore grub with the live cd
If that does not work try [supergrub]("http://supergrub.forjamari.linex.org/") disk
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#15") is some more info on grub error 15

---


---
title: "installing ubuntu on windows with several harddisks"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by baba88 on 2011-01-15
Hi,
I would like to install ubuntu on windows xp which has 6 partitioned hard disks. When I try to install ubuntu on hard disk F, it says i need to select a root. However, I could not succeed in selecting a `root`. 

I also tried wubi, but it was terminated with an abrupt error just before it was finished. 

Furthermore, what does boot directory mean?

Thanks in advance.

---

### Post by Brad55 on 2011-01-15
Linux needs a root and a home partition and the boot loader can be on the first partition where WinXP is. You will have to do the manual set of partitions.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

[http://www.google.com/search?q=install+ubuntu+with+windows+xp&hl=en&prmd=ivns&source=univ&tbs=vid:1&tbo=u&ei=caYxTYrtO4udgQeP4firCw&sa=X&oi=video_result_group&ct=title&resnum=9&ved=0CEoQqwQwCA]("http://www.google.com/search?q=install+ubuntu+with+windows+xp&hl=en&prmd=ivns&source=univ&tbs=vid:1&tbo=u&ei=caYxTYrtO4udgQeP4firCw&sa=X&oi=video_result_group&ct=title&resnum=9&ved=0CEoQqwQwCA")

[http://techblissonline.com/install-ubuntu-on-windows-how-to-vista-xp/]("http://techblissonline.com/install-ubuntu-on-windows-how-to-vista-xp/")

---

### Post by Quackers on 2011-01-15
The /home partition is not mandatory, but the /root partition is ( mount point / )

---

### Post by Brad55 on 2011-01-15
@Quackers This is true I just dont like to put the two on the same partition because if thing go wrong it can mess your data up in /home.

---

### Post by Quackers on 2011-01-15
It is often a good option to have a separate /home partition, it's true. It is just an option though. I have installations with and without a separate /home.

---

### Post by oldfred on 2011-01-15
I prefer to have each hard drive independently bootable. Or the drive with the system has the boot loader in the MBR of that drive. 

Windows confuses things as it calls both partitions and drives as drives. So if F: is really another physical drive, I would install Ubuntu to that drive and install grub to that drive. Then in BIOS change to boot that drive first. Ubuntu will let you boot either Ubuntu or windows and if you ever have drive problems you can still change BIOS and directly boot the windows drive.

Maverick has made it more difficult, as with multiple drives you have to use manual install to get a choice on where to install grub, otherwise it will just install to sda and overwrite the windows boot loader.

Also for any extra drive:
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---


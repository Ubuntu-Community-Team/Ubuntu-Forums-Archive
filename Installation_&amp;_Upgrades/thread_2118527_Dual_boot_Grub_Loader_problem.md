---
title: "Dual boot Grub Loader problem"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by fredsays on 2013-02-21
I had Windows XP and Ubuntu on a dual boot.  I deleted the Ubuntu partiton in error.  Now when booting the process stops with message 'grub rescue'.  I have a copy of current Ubuntu on a CD and booting from CD is activated but it does not load.  Windows XP CD cannot repair the system.  Any advice please

---

### Post by oldfred on 2013-02-21
Welcome to the forums.

From XP disk fixMBR should restore the Windows boot loader to the MBR. What ever is in MBR is tiny and has to jump to more code on drive. When you deleted Ubuntu grub tries to jump to more code in Ubuntu partition that now does not exist.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by fredsays on 2013-02-22
The advice re Windows recovery worked although it was not quite as straightforward as written. Many thanks.  Is it now safe to reinstall a Ubuntu installation, will it load a new dual boot loader without problems?

---

### Post by dino99 on 2013-02-22
when asked, install grub on /dev/sda

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by oldfred on 2013-02-22
As dino99 says be sure to install grub2's boot loader to the MBR of sda not a partition.
All the auto install options will install to sda by default, but manual install or Something else gives the option on where to install the boot loader.
If you want more than the standard / (root) and swap you have to use manual install.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
            [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
    
       Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Install process is not really a lot different between versions, so if you review one or the other the process will be almost identical.

---


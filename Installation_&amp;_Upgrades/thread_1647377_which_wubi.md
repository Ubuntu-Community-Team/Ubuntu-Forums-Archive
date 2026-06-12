---
title: "which wubi?"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by bbala2020 on 2010-12-17
What is the difference between the wubi.exe downloaded from 
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
and the one which is there inside the ubuntu-10.10-desktop-i386.iso ?
Both sizes are slightly different.
I have a windows vista desktop not connected to internet. I can download an iso elsewhere and want to install using wubi. I dont want to burn a cd too.
Is that enough if i download the iso alone and use the installer inside the iso or should i download the installer seperate? Is there anyother thing to be downloaded beforehand for a proper installation? from where?

---

### Post by Megaptera on 2010-12-17
If you install Wubi in Windows it'll download the iso and do the install. If you download the iso not using Wubi, you'll have to burn iso to CD/DVD then run it in Windows and navigate through Windows to the CD/DVD and run it. It'll give you a simple on-screen choice to install within Windows.

If you boot from the CD/DVD you burned, you don't get the option to use Wubi.

---

### Post by bcbc on 2010-12-17
The difference is that the version on ubuntu.com is release 10.04.1.  It will only install Ubuntu 10.04.1
The one in the Maverick release will only install 10.10.

You can place the wubi.exe with the correct release .iso in the same folder and run wubi.exe to install.
You can burn the .iso to CD and open it within Windows to run it.
You cannot expand the .iso to a folder and run wubi.exe within it (it will download another .iso).

Note you cannot install Netbook edition or Xubuntu using the 10.04.1 wubi.exe as there is no 10.04.1 version of these.

If you want to use Wubi, note that it will break if you run updates to packages grub-pc and grub-common. Do not update these (they fall under "Recommended" updates within Update Manager). Never 'reinstall grub' or the 'grub bootloader' - this is commonly used to fix Ubuntu installs, but not for Wubi.

Backup important data.

---


---
title: "how to install vista on preinstall ubuntu pc"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by manish10 on 2014-11-23
Hello Sir,
 I purchased dell laptop with preinstalled Ubuntu linux due to most of the softWARE that runs on windows only i want to make my laptop dual boot so i want to install Windows-Vista on the same without uninstalling Ubuntu , please any one help me , i will be thanful to them , i am also new for linux so i need complete support step by step 
Thanks 
Waiting for the early reply

---

### Post by coldraven on 2014-11-23
I do not know for certain but it may be impossible to install Windows after Ubuntu. It used to be that Widows was installed first and then you could install Ubuntu and have a dual boot machine.
You do not say what Windows software you want to run. Many Windows programs will work if you install Wine. 
See here for a list of programs that will work this way: [https://appdb.winehq.org/](https://appdb.winehq.org/)

Another method would be to run Vista in a virtual machine using VirtualBox. For this to work you would need a reasonably powerful laptop with at least 2GB of memory. 4GB would be better. This also depends on the sort of Vista install disc that you have, the sort with a serial number is the easiest. If you only have an OEM restore disc it can be done but might be too technical for you.

---

### Post by Impavidus on 2014-11-23
You can install Windows after Ubuntu. Use the Ubuntu live disk to create an NTFS partition for Windows, maybe two, so you can use one as a shared data partition. Set the boot flag on the NTFS partition on which you want to install the Windows system. This must be a primary partition and it works best if it is before any logical partitions.

Windows will overwrite the boot loader wih its own boot loader, which cannot boot Ubuntu. Ubuntu's boot loader can boot Windows, so you have to restore the boot loader: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Note: I never tried any of this myself.

---


---
title: "Installing .exe files?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by wok951 on 2008-05-24
Is there a way to install .exe files on Ubuntu? Every time i try to install something it says that the file type is not recognized. What should i do?

---

### Post by Surreal Killa on 2008-05-24
.exe isn't a Linux file type. You can't install an .exe file outside of Windows.

However, there is the program Wine you should look into which will allow you to get some .exes working.

Ubuntu uses .deb files which are installers similar to .exes

To install Wine you can either download a .deb and install or use APT.

sudo apt-get install wine -y

---

### Post by wok951 on 2008-05-24
Where can i get that program?

---

### Post by Aearenda on 2008-05-24
.exe files are for Windows. They don't work natively on Ubuntu or any Linux distribution. You cannot start a program that was previously installed in a Windows partition, from Ubuntu.

What to do:
1. Consider if there is an equivalent program in Linux that you can use, and install that instead using "add/remove..." or System->Administration->Synaptic Package Manager.

2. If you must use a Windows program, check to see if it will work with WINE at [http://www.winehq.org/](http://www.winehq.org/). If it will, you can install Wine on Ubuntu as above, then run the Windows setup program.

3. If the program will not work in Wine, a third option is a Windows virtual system within Ubuntu, using VirtualBox or VMWare, assuming your computer is powerful enough.

---


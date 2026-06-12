---
title: "installing from hard disk"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by orca on 2005-03-14
Hello 

I am trying to install Ubuntu from hard disk. I have a Compaq Armada 1700 with a 160 MB RAM. I will explain what I have done so far and maybe some one can help.

I downloaded the ISO and copied all the files from ISO on to a FAT32 partition. Using a grub boot floppy I booted up my machine. Then I edit the grub to where the boot files for Ubuntu are on my hard drive, i.e. partition 2. 

The system starts booting fine, and then at some point it comes up with a kernel panic and asks to insert the location for “root” in the boot options. I have tried to put root option into the boot menu and tried booting up, but the results are the same. 

I know this method works, because I managed to install Mepis using this. 

If anyone is wondering, why I am not booting directly from CD, because the CD doesn’t work very well and the installation can take more than three hours and sometime half way through the system shuts downs, because it heats up too much. This series of Compaq have a very flaky ACPI support. Before anyone suggest that I should use ACPI=off and/or any other power management options, I have tried them all and they don’t seem to make any difference. 

Hope you guys can help me. 

Thanks

---

### Post by az on 2005-03-14
Yes, it does work.  However, the Warty installer has a problem with doing that.

Try the Hoary installer.  It should work.  Actually, if you do use it and it works, please let me know by replying.  I have never done it myself and this is second-hand information.

If you are really stuck needing Stable packages, use the Debian Woody netinstall iso and dist-upgrade to Warty.  (_That_ I have done)

---

### Post by orca on 2005-03-15
Hi

I have been trying to use hoary installer. It doesn't work. Also, I don't want to use the net install method, as I have limited bandwidth, that is why I downloaded the ISO. 

Thanks

---


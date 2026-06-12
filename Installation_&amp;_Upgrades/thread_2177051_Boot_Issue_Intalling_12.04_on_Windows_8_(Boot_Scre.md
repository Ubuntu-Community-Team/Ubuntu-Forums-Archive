---
title: "Boot Issue Intalling 12.04 on Windows 8 (Boot Screen Illegible)"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by Fabricio_Santos on 2013-09-27
Hello everyone this is my first time posting but I have spent many hours reading thru post to find a solution.  I just purchased a Lenovo idealPad P500 and I am trying to install Ubuntu as a dual boot.  I have read thru the instructions on how to install UEFI.  I have disable Secure Boot and Fastboot.  I am booting from a USB Drive which i used Universal-USB-Installer 1.9.4.3 to mount ubuntu-12.04.3-desktop-amd64 on the memory stick.  
After I have gone into the boot manager and select boot from USB, the computer restart and load Ubuntu but this is what the screen looks like [http://www.dropmocks.com/mBwzup](http://www.dropmocks.com/mBwzup)/.  I also would like to note that I had tried previously to boot Gparted from the DVD/CD drive and I got the same screen, and after that the DVD/CD option has disappeared from the boot menu option.  Thank you and I would appreciate any help.

---

### Post by oldfred on 2013-09-27
What video card/chip does your system have? Often nomodeset works, but some systems need additional or different settings for both video and other boot parameters.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Be sure to boot Ubuntu installer in UEFI mode which will give grub menu. Above shows BIOS menu first and a typical grub menu after install. With UEFI boot you get grub menu as installer.
At grub menu to install in UEFI mode, you press e on menu to edit, scroll down to linux line and replace quiet splash with nomodeset. 

More info in link in my signature.

---

### Post by Fabricio_Santos on 2013-09-27
Thank olfred for all the information.  It seems all I needed to do as hit ctrl-C and enter, when the screen showed up and it took me to the instalation screen.  It dual boot fine and I have ubuntu running on my computer.

---


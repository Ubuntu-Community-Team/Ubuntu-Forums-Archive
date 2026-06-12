---
title: "Adding Win* to Ubuntu 16.10"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by WILLIAM_JAMES_PALM on 2017-01-26
Hello Is it possible to add Win8 to a system running Ubuntu 16.10? I find, and I have done in the past Dual booting Ubuntu to a Windows OS machine. I have been unable to find any document on the internet for doing Windows OS second. Thank You, Wm.

---

### Post by yancek on 2017-01-26
You need to first verify whether Ubuntu is installed using MBR or UEFI/GPT and make sure you install windows in the same manner.  Information on dual-booting Ubuntu/windows UEFI is at the Ubuntu site below including how to determine whether you are using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You need to then use the Ubuntu install DVD/flash drive with GParted partition manager on it to shrink the Ubuntu partition(s) to create unallocated space on the drive on which to install windows.  You will most likely also need to select the Custom install option when booting windows to install. 
 [h=2][/h]

---

### Post by oldfred on 2017-01-26
Some more info:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

If hardware is newer UEFI, you must be sure to boot installer in desired boot mode you want to install.

If BIOS/MBR, the Windows boot loader will overwrite the MBR with its boot loader, you have to reinstall grub.
With MBR, Windows only installs to a primary partitioned formatted with NTFS and that has boot flag.

If UEFI best to let Windows totally partition and install to unallocated space on gpt partitioned drive, it has requirements for multiple partitions.
It will change UEFI boot order to make Windows first. You need to reset if you want Ubuntu first.

If newer Windows 10, you must make sure fast start up is off whether UEFI or BIOS.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by WILLIAM_JAMES_PALM on 2017-01-26
Hello to all and thank you for your comments...Some of what you said is over my head. I think that because I know how to add Ubuntu to a Windows machine, that I will do that, reinstalling Win8 and install Ubuntu 16.10. Thank you all again....

---


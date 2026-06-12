---
title: "Help with GRUB &amp; dual install"
date: 2017-08-30
forum: Installation &amp; Upgrades
---

### Post by PsychedelicWonders on 2017-08-30
I'm rusty and it's been a little while, but I have Ubuntu 16. something on a 128gb SSD and windows on a 256 - Ubutu crashed and I never got it back up and now I'd like to again. 

What's the most stable version right now?

What's the easiest way to fix grub and get the OS bootup menu?

---

### Post by oldfred on 2017-08-30
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Then we can better suggest alternatives.

---

### Post by PsychedelicWonders on 2017-08-31
I don't even think Ubuntu loads up or if it does I don't know the  password.  Wouldn't it be easier for me to just start with a clean  install?

---

### Post by oldfred on 2017-08-31
Sometimes re-install is the easier solution. If you are sure you have no data to recover or have good backups.
But be sure to only use Something Else install option and choose(change button) same /  as new / (root) partition.

If your Windows install is BIOS based be sure to boot Ubuntu installer in BIOS boot mode. Or if UEFI boot Ubuntu installer in UEFI boot mode. 
Most hardware since Windows 8 release date: October 26, 2012 is UEFI, but upgrades from Windows 7 are usually BIOS based boot even on UEFI hardware.

       MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

All recent versions of Ubuntu use same Something Else procedure.  Screens only have changed slightly, mostly colors.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 

[URL="http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using"]
[/URL]

---


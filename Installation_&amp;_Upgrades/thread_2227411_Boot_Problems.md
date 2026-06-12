---
title: "Boot Problems"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by uprise42 on 2014-06-01
First off, sorry if this is the wrong location. If so let me know where i need to be, thank you. 

My problem is i followed instructions on installing Ubuntu onto a laptop with Windows 8. It installed simple enough, and came back successful. Unfortunately when rebooting i had no option to choose which OS to boot into. i booted into the live cd and ran "try ubuntu" and downloaded the boot-repair. It returned this URL [http://paste.ubuntu.com/7568894/](http://paste.ubuntu.com/7568894/) I opened it and didnt understand much so i figured this would be the best place to go. Any suggestions?

---

### Post by oldfred on 2014-06-01
You installed Ubuntu in legacy/BIOS/CSM mode, not UEFI.
UEFI and CSM are not compatible and once you start booting in one mode you cannot change to the other. 
You should be able to go into UEFI/BIOS and choose to boot either Windows or Ubuntu. But you may have to turn on UEFI for Windows and turn off UEFI and turn on CSM mode for Ubuntu. Some auto switch and you can use one time boot key or f12 on many systems.

You can use Boot-Repair to convert to UEFI boot mode. It uninstall grub-pc (BIOS) and installs grub-efi (UEFI), so make sure your Internet is working. And best to always boot in UEFI boot mode. A few systems need major work arounds to work in UEFI mode. What system is this?

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by uprise42 on 2014-06-02
its an ASUS notebook serise

---

### Post by oldfred on 2014-06-02
Some other Asus.

  Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---


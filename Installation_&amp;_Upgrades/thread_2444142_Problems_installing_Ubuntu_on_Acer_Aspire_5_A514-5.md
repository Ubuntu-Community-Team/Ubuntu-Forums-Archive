---
title: "Problems installing Ubuntu on Acer Aspire 5 A514-52"
date: 2020-05-25
forum: Installation &amp; Upgrades
---

### Post by tomsax on 2020-05-25
I'm having difficulty installing Ubunto on the a new Acer Aspire 5 A514-52

During installation it tells me the laptop has RAID and points me in the direction of instructions here:  
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

I follow the intructions and as it suggests might happen, it still has problems rebooting.  To resolve this it gives instructions on doing something to the boot partition but here it is difficult to follow or I just don't understand.  I tried to edit the boot partition but it still doesn't boot.

I here attach some images

[ATTACH=CONFIG]286011[/ATTACH][ATTACH=CONFIG]286012[/ATTACH][ATTACH=CONFIG]286013[/ATTACH][ATTACH=CONFIG]286014[/ATTACH][ATTACH=CONFIG]286015[/ATTACH]

Any guidance on what I need to do to get through this problem appreciated.

Tom

---

### Post by oldfred on 2020-05-25
Often easier with UEFI Secure Boot off. Screen 3.
Probably your Optane setting, drives need to be AHCI. Screen 5.

General UEFI info in link in my signature.

Issues often common by Brand, so probably similar:
You may need UEFI update & SSD firmware update first.

Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
acer predator helios 300 PH 315-51 i5 8th gen
[https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli](https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli)
Acer Predator Helios 300 Boot into system, update, reboot then install drivers.
[https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace](https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace)


Most Acer needed "trust" setting after install.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by tomsax on 2020-05-27
Went through a lot of the instructions but Windows is still not rebooting after I change drive to AHCI.  

i haven't got time at the moment to go through everything I've done,, maybe tomorrow night.  I did manage to shrink the windows partition using windows disk management but that is all I seem to have achieved.

I don't want to install ubuntu until I am sure Windows will boot properly as want to set up dual boot.

Or is the idea I can change back from AHCI after installing Ubuntu?

---

### Post by ubfan1 on 2020-05-27
No, you need to install the ahci drivers in Windows, and leave them there.

---

### Post by oldfred on 2020-05-27
Several sets of instructions on changing AHCI.
You can change back to Intel SRT, but  then Ubuntu will not work. So have to convert Windows to use AHCI.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by tomsax on 2020-05-29
I've now managed to install Ubuntu on the Acer machine.

Following the instructions in here I finally managed to do it 
[https://askubuntu.com/questions/1148...g-installation](https://askubuntu.com/questions/1148...g-installation) 
but following Choice #2 not Choice #1.  

I tried to follow Choice #1 first but ended up having to reinstall Windows using a recovery stick that I had prepared (do prepare this as they suggest just in case).

Thank you Oldfred for your help on this.  

I think the earlier instructions in [https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
should have worked as they look similar but I may have made a mistake.  It could be just that it wasn't clear how to enter Windows Command Prompt as Adminstrator and in the second link this is more clearly explained.  Some of us need lots of help.  I didn't have to use windows disk management to shrink the Windows drive as this was done with the Ubuntu installation procedure.

I think Windows is working with no problems.  My son reckons it is slower downloading and installing stuff now but I'm pretty sure this is his imagination.

I have a follow on problem in that although Ubunto 20.04 is nicely installed, the wifi is not working.  It says it is on the icon in the top right but opening Firefox nothing can open.  Hope this can be solved.  I will open another thread for this in the other network issues forum or whatever it is.

Thanks again.

Tom

---


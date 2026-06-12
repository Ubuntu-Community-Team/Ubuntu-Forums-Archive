---
title: "Cannot boot for upgrade"
date: 2020-08-26
forum: Installation &amp; Upgrades
---

### Post by torbentf on 2020-08-26
Hi,
I have tried to install 18.04 and 20.04 from a USB CD-ROM  (I have done that before with 18.04) but all I get is the Acer logo and the following text in the upper left corner:

System boot order not found. Initializing defaults.
Creating boot entry "Boot173" with label "ubuntu" for file "/EFI/ubuntu/shimx64.efi" 
Reset system

Then the computer shuts down and the process is repeated (except the "Boot173" becomes "Boot174" etc.)

I have the CD-ROM reader as first choice in boot sequence and I suppose it should provide the boot record for the installation.
I normally have an EFI boot installed.

I think I have tried everything to break the sequence, but nothing has worked.
I have tried to reset the computer to factory standards, but none of the methods found on Internet works.
Can anyone help?
Best regards
torben

---

### Post by GhX6GZMB on 2020-08-26
I hope you mean DVD-ROM?

---

### Post by torbentf on 2020-08-26
Hi,
Yes
torben

---

### Post by oldfred on 2020-08-26
What model Acer?
Many Acer require you to set "trust" for ubuntu entry in UEFI.

Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
acer predator helios 300 PH 315-51 i5 8th gen nouveau.modeset=0
[https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli](https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli)
Acer Predator Helios 300 Boot into system, update, reboot then install drivers.
[https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace](https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by torbentf on 2020-08-27
Hi,
The only way I can see as a novice is using the boot-repair.  However, I suspect both my dvd reader and my computer. I have tried to  put the boot repair (ISO) on dvd[I]. should that boot? Well, it dont. Iwould like to put the ISO file on my Verbatim usb stick, but I cant see how I do that. 
Can you help?
torben
[/I]

---

### Post by oldfred on 2020-08-27
Do not use Boot-Repair ISO as it is not the most current version.
Use your Ubuntu live installer and add the Boot-Repair ppa as shown in the Boot-Repair link.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

All Linux ISO have to be extracted and converted to be bootable. If UEFI system, the /EFI/Boot folder already exists. But if BIOS/CSM/Legacy a boot loader is also added as part of process of creating a bootable DVD or flash drive. Many tools now use the hybrid DVD/Flash drive configuration that the ISO is to create a bootable device and that has everything you need.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by torbentf on 2020-08-28
Hi oldfred,
That helped. Thank you very much.
I hoped I used the Thread Tools correctly.
torben

---


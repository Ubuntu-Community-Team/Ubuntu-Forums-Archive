---
title: "noob needs help with instalation"
date: 2021-12-03
forum: Installation &amp; Upgrades
---

### Post by feferonn on 2021-12-03
Hi,

First I would like to aplogise for not so great English or my tehnical knowlage(lack of it) of Linux. I installed windows from usb few times, thought it will be simple as that. I'm hoping some1 will spot something basic I missed.

I have HP Notebook - 17-x108nm ([https://support.hp.com/hr-en/document/c05380278](https://support.hp.com/hr-en/document/c05380278)) and i have windows10 instaled. Wana try something different.

So i downloaded 21.10 flashed it on usb(with rufus) went to laptop, went to bios, changed boot order, saved and restarted. Before ubuntu logo came, there were errors:

ACPI Error: No handler for Region [ECF2]...(few more lines with some region)
drm:amdgpu_init [amdgpu] *ERROR* VGACON disables amdgpu kernel modesetting.
[sdb] No Caching mode page found
[sdb] Assuming drive cache: write through

Few seconds later there i could select:
ubuntu
ubutnu(Safe graphics)
and 2 others(like firmware, uefi, not 100% sure )

Clicked on unbutu, installer opened and froze 2 steps in.(Where i choose language/keyboard). So i restart and select unbutu(Safe graphics) and on 3.step it froze(Where it asks to connect to internet)
So I went and googled, went back to BIOS (InsydeH20 setup utility) enabled some Legacy Suport and disabled secure boot, turned on some virtualization tehnology and restarted. Didnt help, this time i got stuck some step leater(where it asks if i want some minimal instal etc)

So downloaded 20.04 and flashed on other usb (with BalenaEtcher), stuck it in laptop and this time, same errors, but this time there was some checking disk before.(and this time, sometimes after selecting ubuntu screen would stay black)

So booted windows, used some tool Unetbootin and now when i restart laptop it asks to start win10 or unetboot, if i select unetboot it says _*Windows*_ failed to start...

Since i saw this model with Mint i tought it's linux suported.

I would appreciate some advice.(and sorry if i broke some forum rule/ posted in wrong section), i tried more then 8 times with bouth usb(with and without safe graphics)

Best regards,
Mijo

---

### Post by oldfred on 2021-12-03
Do not turn on Legacy support. 
Windows will be in UEFI boot mode and to easily dual boot you need Ubuntu in UEFI boot mode.

You do need drive in AHCI mode, Windows fast start up off, and often easier to have UEFI Secure Boot off (but not required). 
HP's often are not easiest to work with, but do work. 
You need to make sure UEFI is most current version firmware and if SSD, that SSD has latest firmware.
Once installed, HP will  only change boot mode from UEFI settings menu (not UEFI boot menu). HPs just do not support UEFI boot order change using efibootmgr which grub uses to install grub boot loader. Virtually all other systems seem to work with efibootmgr.

Some general UEFI install info in link in my signature below.

---

### Post by feferonn on 2021-12-05
Turned off Legacy support, had to check what AHCI is and how do i check is it on(it was)
While I was trying to figure out uefi/ssd firmare i saw BIOS last update was 2016, so i updated it and now it works. 
Thanks for help. :)
(Now i'm stuck where i'm choosing partition where to instal, but i'll figure it out(some root file sys is not defined etc))

---

### Post by yancek on 2021-12-05
>  (Now i'm stuck where i'm choosing partition where to instal, but i'll figure it out(some root file sys is not defined etc)) 		 	  	 		 		 

Take a look at the tutorial at the link below, Section 4.b where it discusses creating partitions, you need to enter the mount point for the root filesystem which is the "/" symbol as shown.

[https://ubuntuhandbook.org/index.php/how-to-install-ubuntu/](https://ubuntuhandbook.org/index.php/how-to-install-ubuntu/)

---

### Post by feferonn on 2021-12-07
After reading some guides i figured it out, instalation started and installation bar went to end with "Almost finished copying files..." msg above and after 10h it was still there at "Almost finished"

I guess i'll try with new/bigger usb and try again.

---


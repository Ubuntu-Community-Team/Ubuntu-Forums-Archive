---
title: "problem in dual boot in uefi"
date: 2022-04-20
forum: Installation &amp; Upgrades
---

### Post by hu016865 on 2022-04-20
[FONT=Roboto, RobotoDraft, Helvetica, Arial, sans-serif][COLOR=#000000]I have a Sony svf 1521 laptop that support uefi,[/COLOR][/FONT]
[FONT=Roboto, RobotoDraft, Helvetica, Arial, sans-serif][COLOR=#000000]I just bought a SSD evo 870 Samsung and i want to dual boot Linux and windows 10.I installed Windows without any problems in uefi mode and gpt partitioning, I also installed Ubuntu 21.10 in free space, by creating /efi /root /home partitions, 
during the installation, I was asked about secure boot, which I unchecked ( Because Wi-Fi does not work when secure boot is enabled)When the installation is complete and I restart, Linux will boot, but after the next restart, only Windows will boot and Linux will not work.Is it possible to install Windows and Linux dual boot in uefi mode without any problems?[/COLOR][/FONT]

---

### Post by oldfred on 2022-04-20
Did you create two ESP's on same drive?
Many UEFI systems do not support that. But once each ESP - efi system partition (FAT32) set up, it may continue to work until updates.

Some systems require you to change boot order in UEFI settings (not UEFI boot menu).
And grub only boots working Windows. That includes Windows cannot need chkdsk nor is hibernated. Fast startup sets hibernation flag, so it must be off. Newest grub may have os-prober turned off, so may not then add Windows to grub menu.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by hu016865 on 2022-04-21
[COLOR=#000000][FONT=Roboto]After installing Windows, the efi partition will be created. I did not create this partition at the time of Linux partitioning, but the problem still remained.[/FONT][/COLOR][COLOR=#000000][FONT=Roboto][/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Do I have to mount the built-in efi when Linux partitioning?[/FONT][/COLOR][COLOR=#000000][FONT=Roboto][/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Because I am a beginner I need more explanation[/FONT][/COLOR][COLOR=#000000][FONT=Roboto][/FONT][/COLOR][COLOR=#000000][FONT=Roboto]And I do not know English well and I use Google Translate.[/FONT][/COLOR]

---

### Post by yancek on 2022-04-21
Your best next step is to go to the link for Boot-Repair posted above in post number 2.  Read through the page and use the 2nd option explained on that page to download and run boot repair by selecting to Create BootInfo Summary and post the link you get when it finishes here.  That will give more details on the status of your system and you should be able to get some help.

---

### Post by hu016865 on 2022-05-06
I solved part of my problem with the help of a friend in the Iran Ubuntu forum, which was related to not activating Wi-Fi after entering Ubuntu by updating the policy. 
> sudo update-secureboot-policy --enroll-key 
After logging in to Ubuntu, you no longer need to disable mokutil. This is the explanation for my problem with Wi-Fi:
> Your WiFi driver is not included with the kernel. (Because of its license. Broadcom has a strict license for it)
Because it does not come with the kernel, it is compiled separately.
When compiled separately, it has no signature. 
When secure boot is enabled, the kernel does not load modules that do not have a valid signature (or do not have a signature). The result is that your WiFi does not work. 
You can turn off secure boot and then this module will load without any problems and your WiFi will start working. 
But the second problem: 
when I enter Windows from the Grub menu, after turning off or restarting the laptop, the Grub menu is removed and I enter Windows directly. To solve this problem, I have to enter the bios menu once and change uefi to legacy, restart the laptop to see the grub menu again.

---

### Post by tea for one on 2022-05-06
> **hu016865 said:**
> Is it possible to install Windows and Linux dual boot in uefi mode without any problems?
Yes, it is certainly possible.
> **hu016865 said:**
> when I enter Windows from the Grub menu, after turning off or restarting the laptop, the Grub menu is removed and I enter Windows directly. To solve this problem, I have to enter the bios menu once and change uefi to legacy, restart the laptop to see the grub menu again.
As requested by [COLOR="#0000FF"]oldfred[/COLOR] in post 2 and [COLOR="#0000FF"]yancek[/COLOR] in post 4, please supply the details from the boot-repair utility.
This report will help to identify the problem and allow forum members to offer advice.

---

### Post by hu016865 on 2022-05-06
sloved with this command in windows 10
> bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

---


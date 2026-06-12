---
title: "grub-efi-amd64 failed to install"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by Gildon on 2014-02-01
Hello. I have looked around the forums for a solution to this problem but I kinda new to linux and I don't think any of them solved it. I'm trying dual boot Kubuntu with my already installed Windows 7. I have two hard drives but I unplugged the one for storage in order to simplify the installation process. On my main hard drive, an SSD, I have Windows 7 already installed. I believe it installed in legacy BIOS mode, not UEFI because if I try to boot exclusively with UEFI, the boot fails. The main hard drive is partition like this: 
/dev/sda
-/dev/sda1  ntfs      Windows system partition
-/dev/sda2  ntfs      Windows 7 partition
-/dev/sda5  ext4     Desired Kubuntu root installation /
-/dev/sda6  ext4     Desired Kubuntu /tmp directory 
-/dev/sda4  swap

I have a feeling that my problem lies in the fact that windows originally installed with the BIOS, not UEFI so I won't be able to boot from a UEFI grub. Also I read somewhere that people solved this problem by ensuring they were connected to the internet. That might be my problem as well as the Kubuntu live CD doesn't seem to recognize my wireless adapter. Thanks for the help.

---

### Post by ajgreeny on 2014-02-01
Have you seen and read fully all the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which may be useful to figure out in what manner your system is booting Windows 7.  You may also get enough info from this to change the Ubuntu boot method, though if it's a non-used Ubuntu OS so far it may be easier to start again and boot the install medium (USB or DVD) in legacy mode, then install from that live setup.

---

### Post by oldfred on 2014-02-01
You cannot install Windows in BIOS and Ubuntu in UEFI on the same drive. 
BIOS boot requires MBR partitioning and UEFI boot requires gpt partitioning.

While possible to have different boot modes if two drives, better to either have both systems UEFI or both systems BIOS. 
If different you cannot dual boot from grub menu, but only from UEFI menu. And may have to turn on/off UEFI or on/off for Legacy/BIOS/CSM boot before changing systems.

---

### Post by Gildon on 2014-02-01
Okay, thank you. I got the system up and running by forcing the cd to boot from bios mode.

---


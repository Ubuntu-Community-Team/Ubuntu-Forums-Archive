---
title: "My first EFI install, comments and questions"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by Luke M on 2014-03-26
I did an EFI install of ubuntu 14.04b1 (my first) and have a couple of observations and questions.

1. During the install, there's an option to select the boot drive or partition. I selected a partition I wanted and marked it as an EFI type, but the installer didn't use it. It used another EFI partition instead - maybe it always uses the first one? Are you supposed to be able to select the EFI partition (when there's more than one) you want it to use?

2. For some reason my firmware now has two "ubuntu" boot options, not one. It's like the installer added it twice (and my firmware wasn't smart enough to detect the duplication).

3. A BIOS-loaded version of Windows on the machine was not added to the grub menu. I guess grub doesn't support that? (Or maybe it's impossible to switch to BIOS from EFI?). It did find all the other OSes (linuxes and EFI Windows), good job.

---

### Post by fantab on 2014-03-26
You should have only ONE ESP [EFI System Partition] per HDD.

Your 3rd point is confusing. For EFI boot it is imperative that you have GPT disk. If you have a GPT disk then "A BIOS-loaded version of Windows" is NOT possible on that disk. If you have non-GPT, msdos/MBR disk then EFI is impossible.
Can you post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Luke M on 2014-03-27
> **fantab said:**
> 
Your 3rd point is confusing. For EFI boot it is imperative that you have GPT disk. If you have a GPT disk then "A BIOS-loaded version of Windows" is NOT possible on that disk. If you have non-GPT, msdos/MBR disk then EFI is impossible.


It's on a different disk.

---

### Post by fantab on 2014-03-27
It is not at all a good idea to have 'mixed' boots. All your OS should either be installed in UEFI or BIOS modes. Grub has both BIOS version and EFI version. 
If and when ESP is present then grub_efi is installed otherwise its just legacy grub.
You currently have grub_efi so bios mode is not possible.

However, I think, you can boot the BIOS mode Windows directly from the UEFI boot menu....

---

### Post by sudodus on 2014-03-27
It is possible to have a mixed boot. I agree that it is not a good idea to have such installed systems, but it can be useful to have such a USB pendrive, to be able to boot many computers. See this link

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by oldfred on 2014-03-27
The main reason not to have mixed boot is that you can only select which system to boot from UEFI, not from grub. Some can use one time boot key like f12 on my system. Others have to manually switch UEFI on/off or BIOS/CSM on/off each time.
UEFI & BIOS are not compatible, so once you start booting in one mode you cannot switch. Or once at grub menu you cannot boot another system unless in same boot mode.

Ubuntu will boot in BIOS mode from gpt partitioned drives and you can convert a UEFI boot Ubuntu on a drive to BIOS boot. Boot-Repair -advanced options is probably the easiest way as it automates the uninstall of grub-efi(UEFI) and reinstall of grub-pc(BIOS). Before running Boot-Repair you have to create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive. Use gparted to create it.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Luke M on 2014-03-27
I would prefer to avoid EFI, but since I have Windows installed on a >2TB drive, I have to use it (Windows, unlike grub/linux, doesn't allow legacy BIOS boot on a GPT drive).

---

### Post by oldfred on 2014-03-27
So do you have two Windows installs, one UEFI and one BIOS?
May be best to see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)
Script to semi-automate efibootmgr changes -  user slooksterpsv  in forums
[https://launchpad.net/~slooksterpsv/+archive/efibootorder](https://launchpad.net/~slooksterpsv/+archive/efibootorder)

---

### Post by fantab on 2014-03-27
> **Luke M said:**
> I would prefer to avoid EFI, 

You cannot avoid EFI for long. It IS the replacement for BIOS. Mobo manufacturers are not using BIOS anymore. Lets get used to EFI and GPT. Also with GPT you can easily use more than 2Tb HDD, which with MBR we cannot.
[http://cache-www.intel.com/cd/00/00/33/44/334412_334412.pdf](http://cache-www.intel.com/cd/00/00/33/44/334412_334412.pdf)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

---

### Post by Luke M on 2014-03-27
> **oldfred said:**
> So do you have two Windows installs, one UEFI and one BIOS?


Yes.

I managed to delete the duplicate ubuntu boot option, but I wish it were easier to add/delete them. EFI strikes me as a fragile system, since it places critical boot information in "NVRAM" rather than on the disk. Tools like rEFInd mitigate the problem some.

---


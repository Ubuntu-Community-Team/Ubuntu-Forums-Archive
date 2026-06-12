---
title: "Default EFI install fails to boot on Lenovo T540p"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by bhron on 2014-12-21
Hi, I recently installed ubuntu with manual partition configuration on a system have no other OS. In the installer, I specified manual partitions and created an EFI partition at the start of the drive (200MB). There were two problems with the default EFI partition:

1. The partition type was not set to "EFI System". I had to boot from liveUSB and change it with fdisk.

2. Grub was written to** /boot/EFI/ubuntu/grubx64.efi**. Please be aware that [COLOR=#ff0000]**not all firmware will see this file!**[/COLOR] My new Lenovo T540p (arrived 2014-12-19 from the manufacturer) requires grubx64.efi to be copied to **/boot/EFI/boot/bootx64.efi**. 

Before I fixed these problems, the system would not boot past BIOS, and gave no errors or warnings of any kind. Please consider updating the installer to (1) create the correct partition type for EFI partitions, and (2) duplicate the grub .efi file as .../EFI/boot/bootx64.efi if no such file exists already (and maybe warn?overwrite if it does). *It would have saved me 8 hours of totally wasted time.* Thanks.

---

### Post by oldfred on 2014-12-21
If you were able to use fdisk, then it is not a UEFI install.
Fdisk is for MBR partitioned drives and UEFI uses gpt partitioned drives, use parted or gdisk.
You may just have a standard BIOS boot install and then would need BIOS set to boot in CSM/Legacy/BIOS boot mode not UEFI?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajgreeny on 2014-12-21
If you had chosen to install using the whole disk and not specifying partitions manually I believe the system would have set everything up as needed.  You chose however to partition manually and therefore the system installed exactly as you told it to, and whilst I accept it would be good to have some way to be made aware that your choice is incorrect, I think you will have a long wait for that.

With regard to your point #2, grub could not be written to/boot/EFI/ubuntu/grubx64.cfg because that pathway depends on having a valid and working EFI partition, which you did not have.

Sorry to say this but before starting you should have read around the subject and tried to fully understand what you were trying to do; all the info you needed is easily available in the community help at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, after that slight admonition, welcome to the Ubuntu forum, which I hope you will find is a very useful place to visit when you need  information about this terrific OS.

---

### Post by bhron on 2014-12-21
> **oldfred said:**
> If you were able to use fdisk, then it is not a UEFI install.

You can definitely edit UEFI parittions with fdisk. There is even an option in fdisk to set the partition type to "EFI System". The fdisk commands are slightly different for a GPT (e.g., no "a" option to set the boot flag), but it certainly works. 

It is certainly a bug in the Lenovo firmware to look only for EFI/boot/bootx64.efi. But the fact remains that it is a treacherous situation and not at all uncommon. I strongly recommend handling bad firmware, even though it is bad. The users can't do anything to improve their firmware, so we might as well accommodate.

---

### Post by oldfred on 2014-12-21
The bootx64.efi is a hard drive boot entry. With older versions of UEFI, that was only for external devices. But newest UEFI allows /EFI/Boot/bootx64.efi to boot from a hard drive.

Most vendors have modified UEFI to only boot a Windows description type (and hard drive) entry.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---


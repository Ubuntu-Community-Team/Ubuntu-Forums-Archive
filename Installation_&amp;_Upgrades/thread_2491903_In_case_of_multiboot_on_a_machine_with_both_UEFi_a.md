---
title: "In case of multiboot on a machine with both UEFi and legacy BIOS, which is better to"
date: 2023-10-25
forum: Installation &amp; Upgrades
---

### Post by zoli62 on 2023-10-25
Asking my question is justified by a case I experienced a few days ago. My Lenovo laptop has three Linux distributions (MX Linux, Kubuntu LTS, EndeavorOS) and Windows 10 installed with UEFI. I use EOS's grub as bootloader, although on Kubuntu the occasional grub package updates (os-prober enabled) overwrites the kernel entries for EndeavourOS, and in this case EOS is unbootable, you have to re-edit Kubuntu's grub.cfg for EOS according to the kernel entry in  EOS grub.cfg (initrd ->initramfs). Last time I updated Windows 19 to the latest release. after i restarted the machine, i was greeted by grub rescue. Although you can reset the boot order here as well, I didn't do that. At the next startup, I selected Kubuntu from the temporary startup menu, then reinstalled grub and updated the settings. Then, of course, grub.cfg had to be modified for EOS as described above. Then I restarted the machine again and started EndeavorOS from the Kubuntu grub. After logging in, I reinstalled grub using jtt us and then updated the settings. After that, I was able to start the machine with the EOS grub. By the way, it is recommended to create a separate ESP partition for each OS just for such cases. Another laptop has only BIOS and windows 10 with a linux and the windows edition upgrade had no problem..I asked this question here because I read that the Windows version update tends to cause problems with grub installed in MBR with the legacy BIOS, but mostly not with UEFI.

---

### Post by yancek on 2023-10-25
Some windows updates on UEFI systems will turn on Secure Boot, set windows to first option in the boot order and turn on hibernation.  These can all cause problems on multiboot systems.  Hibernation will only be problematic if you try to access a windows filesystem from Linux as it won't work when windows is hibernated.  It should be simple to move windows down in the boot order.

Many Ubuntu distributions have a directory on the EFI partition named 'ubuntu'.  If both Kubuntu and Endeavour use 'ubuntu' rather than a directory name specific to the OS, any time you update Grub on the system, it will overwrite what is currently there.  Take a look at the /boot/efi/EFI directory to see if you have separate directories for Kubuntu and Endeavour or only ubuntu.

You don't want more than one EFI partition, particularly on a single drive, what you should have is separate entries (directories) for both Kubuntu and Endeavour so when Grub is updated from one system, it does not overwrite the other systems files.

---

### Post by tea for one on 2023-10-25
> In case of multiboot on a machine with both UEFi and legacy BIOS, which is better
Uefi is better:-
Faster boot time
Secure boot is available (if required)
Support for hard drive partitions larger than 2TB
Support for more than four primary partitions on a drive
Allows booting from EFI shell
Alternative boot managers e.g. rEFInd (even via portable USB)
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

> **zoli62 said:**
>  By the way, it is recommended to create a separate ESP partition for each OS just for such cases.
> **yancek said:**
> You don't want more than one EFI partition, particularly on a single drive, what you should have is separate entries (directories) for both Kubuntu and Endeavour so when Grub is updated from one system, it does not overwrite the other systems files.

So far, within 2000+ pages of the UEFI specification, [https://uefi.org/sites/default/files/resources/UEFI_Spec_2_10_Aug29.pdf](https://uefi.org/sites/default/files/resources/UEFI_Spec_2_10_Aug29.pdf), I’ve not been able to pinpoint which is correct.

Many UEFI settings and features are afforded and constrained by the vendors’ UEFI firmware configuration. 

Just to offer an example where two ESPs on one drive offer an OS choice advantage:-

Intel NUC6 Desktop PC with one disk SSD 120GB
Windows 11 and Ubuntu dual boot

[COLOR="#0000FF"]One ESP[/COLOR] - to boot the PC via one-time (F10 for Intel) boot menu
UEFI: SATA: Port 0: Sandisk SDSSDHII1 120G
Only the disk is listed and then it boots to Grub

[COLOR="#0000FF"]Two ESP[/COLOR] (one for Windows and one for Ubuntu) via PC boot menu (F10)
UEFI: SATA: Port 0: Windows Boot Manager
UEFI: SATA: Port 0: Ubuntu
Windows Boot Manager avoids Grub
Ubuntu boots to Grub (where I've allowed OS_PROBER to find Windows)

In this case, two ESPs offer a distinct advantage i.e. Windows is available if Grub is compromised.
Whether this survives future UEFI, Windows and Ubuntu updates – who knows?

---

### Post by oldfred on 2023-10-25
A lot of UEFI implementations, do not allow more than one ESP per device.
I have found that grub works to find ESP boot entries in a FAT32 partition. So possible to move esp,boot flags to a second ESP, install UEFI boot files and move flag back to first ESP. UEFI entry finds GUID, grub finds other systems.
Its just during install of boot loaders the esp,boot must be the correct partition. Ubuntu does assign ESP in fstab, so after first install, I am not sure it matters after first install. 

I normally suggest one ESP per drive, required for external drives.
But Ubuntu's Ubiquity has wanted to only install to first drive's ESP.

---

### Post by zoli62 on 2023-10-25
[COLOR=#3C4043][FONT=Roboto]Only MX Linux has things in the boot/efi/EFI directory, the other two distros don't. By the way, I just installed grub on it, because it looks like it better handles the rewriting of kernel entries that occurs in Kubuntu during grub package updates. [/FONT][/COLOR][COLOR=#3C4043][FONT=Roboto]That is, even though os-prober is enabled, MX does not touch grub.cfg's kernel entries for EndeavorOS so harshly.[/FONT][/COLOR]

---

### Post by zoli62 on 2023-10-25
Yes, there are different tactics to avoid inconveniences after periodic updates. In fact, the BIOS is also an alternative to boot management.

---

### Post by MAFoElffen on 2023-10-25
For a while, I was setting up all my own root disks as GPT & dual-boot for Grub2. So that no matter what machine they were on and what the BIOS boot modes that machine supported, that they could boot.

I don't do that anymore. I just set them up to boot for UEFI boot mode. There is so many features and advantages to that mode that it would fill volumes just list them.

I'll leave it at that.

These days, it just doesn't make common sense to set something up with an MS-DOS disk partition type, nor as BIOS Legacy Boot. Many vendors that used to offer their BIOS with options to boot from either, do not anymore on their newer machines. They are trying to phase that out and let that be something from the past. Eventually it will be.

---

### Post by zoli62 on 2023-10-26
Maybe it's best to have UEFI boot as well as Grub. When the latter "breaks down" for some reason, the machine can still be started with the former. After the latest Windows feature update that resulted in grub rescue, it was also useful for me to have UEFI boot.

---


---
title: "Converting my legacy mode installation of Kubuntu to UEFI alongside OEM Windows8"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by Nishad_Kadam on 2014-09-21
[SIZE=3]I am new to linux and UEFI. you can assume that I no nothing about UEFI and how to handle it.
I have installed Kubuntu in legacy mode on my hp pavilion g6 laptop alongside preinstalled Windows 8 (UEFI). I want to convert my Kubuntu installtion to UEFI. 
I have read the official ubuntu documentation related to UEFI which involves using boot repair software on ubuntu. I have some questions related to that as follows:

1) What does this process exactly do? I mean what changes in the EFI partition this process will do..
2) If this process stucks or fails or completes with errors, no doubt it will screw up both windows and Kubuntu. So is there an escape plan or simply plan B, which I can understand?
3) If I want to reinstall the Kubuntu, how to do it and how to wipe the old entries? 
4) If I windows deletes the grub, how to reinstall it? 

 I have read many articles and for me, the most important thing is your experience, so share it...
 [/SIZE]

---

### Post by Vladlenin5000 on 2014-09-21
AFAIK you can't convert one into other.

---

### Post by fantab on 2014-09-21
It can be done. Boot-Repair removes grub-pc and installs grub-efi. In Boot-repair you have to choose 'Advanced Options' -> Grub location -> select separate EFI boot partition and select your ESP.

If in doubt, Post the output of the following:
```
sudo parted -l
```

---

### Post by oldfred on 2014-09-21
As long as drive is gpt partitioned it can be done. And if Windows 8 pre-installed by a vendor it will be UEFI with gpt partitioning.

With UEFI each system installs a new folder into the efi partition with its boot files. The efi partition replaces the MBR. But with a MBR you only have one per drive so only one system can boot. With the efi partition, UEFI will list all the installs or each folder in the efi partition and let you choose which to boot and you can set one as default.  But some vendors modify UEFI to only use the entry with Windows in the description. But we have work arounds for those systems.

Best to also back up efi partition as well as your entire Windows install.

Currently if reinstalling, only use Something Else. There is a bug where it may say it is replacing Ubuntu (or Kubuntu) but erases entire hard drive. With Something Else you have total control over which partition is used (or reused) as / (root) and /home.

If Boot-Repair offers to rename files, do not do it. It is one work around but others are better now. 
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

---


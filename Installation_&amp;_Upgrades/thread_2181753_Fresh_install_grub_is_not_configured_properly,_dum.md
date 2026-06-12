---
title: "Fresh install grub is not configured properly, dumped to grub shell (UEFI)"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by FuturePilot on 2013-10-18
I just did a fresh install of 13.10 alongside Windows 8 and grub seemed to install fine but it's not configured right. I'm dropped immediately into a grub shell and I must run the following to get the grub menu to display

```
configfile (hd0,gpt1)/efi/kubuntu/grub.cfg
```

Then the menu comes up and I can boot normally. Why is it not picking up the config file by itself? I'm lost when it comes to how UEFI works.

---

### Post by oldfred on 2013-10-19
I did not think grub.cfg was in efi partition. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ubfan1 on 2013-10-19
I'm not familiar with Kubuntu, but for Ubuntu, the grub.cfg file (should be a 3 line stub bringing in the maintained grub.cfg from /boot/grub) is located in (EFI partition) /EFI/ubuntu/grub.cfg.   This is the location grubx64.efi examines for it, so don't know if it also examines /EFI/kbuntu.  Try making an ubuntu directory and putting in a copy of the grub.cfg.

---

### Post by FuturePilot on 2013-10-19
> **oldfred said:**
> I did not think grub.cfg was in efi partition. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

The grub.cfg file that is in the EFI partition is just a stub that points to the full config file that is on the root partition. Here is the output from boot-repair

[http://paste.ubuntu.com/6264913/](http://paste.ubuntu.com/6264913/)

---

### Post by oldfred on 2013-10-20
Yours is the first I have seen with the bug fixes to the grub2's os-prober. Boot-Repair then does not have to add the additional boot stanzas in 25_custom unless it is a buggy UEFI where the Windows efi file has to be renamed.

The buggy UEFI issue is that some vendors have modified UEFI to only boot the Windows file with secure boot on. But since grub2's shim file has the Microsoft signing key it will boot if it has the Windows name. So the work around is to rename shim to be Windows and boot into grub and from grub boot a backup copy of the actual Windows file.

You have the signed versions installed so you should be able to boot with secure boot on or off.

I do not think an ubuntu folder is needed. With UEFI you can have an unlimited (except for space) number of folders each with different boot files. UEFI then should offer to boot from each folder.

I do not know details, but some UEFI still have issues. Do you have the latest UEF/BIOS from vendor.
Some have also found that rEFInd helps. It is another boot manager. Both UEFI and grub act as boot managers, but grub also is a boot loader.

       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by ubfan1 on 2013-10-21
@oldfred: I think the /EFI/ubuntu folder is the place grubx64.efi looks for the grub.cfg file.  Putting grub.cfg in the same directory as grubx64.efi did not work for me (think I tried the /EFI/Boot directory).

---

### Post by FuturePilot on 2013-11-01
Looks like it was this bug. [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417")

I was somehow able to get it working a while ago with boot-repair. I think it had something to do with that it created an /efi/ubuntu/ dir but it should be fixed properly now according to the above bug report.

---


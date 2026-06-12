---
title: "No GRUB on Startup"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by nyren-amyra-dael on 2013-11-11
I am pretty new to Linux and I already prefer it to Windows, but I still need it for various applications. Partitions don't entirely make sense to me because I have a few which are not identified and everyone on the internet seems to already understand them. Anyways, I successfully created a Ubuntu and swap partitions both following the Windows C: drive partition. If I press F9 on my HP Pavilion Sleekbook 14-b017nr, I have OS Boot Manager which leads to Windows 8 and ubuntu and Ubuntu which both lead to the GRUB menu. My computer automatically boots into Windows. How Can I fix this? Willing and open to all suggestions. (As long as you know what you are taking about) Thanks!!

---

### Post by oldfred on 2013-11-11
Is your system UEFI or BIOS? And are both systems installed in the same mode.
 May be best to see details.

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

### Post by nyren-amyra-dael on 2013-11-11
[http://paste.ubuntu.com/6401728/](http://paste.ubuntu.com/6401728/)
Link created by boot-repair info.

---

### Post by nyren-amyra-dael on 2013-11-11
Just ran the recommened repair. Still does not boot correctly. Now there is only Ubuntu uppercased in the boot manager and tons of stuff in the grub menu.

 Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6401856/](http://paste.ubuntu.com/6401856/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by oldfred on 2013-11-11
Do you have secure boot off? And fast boot? If you go into UEFI menu or from one time boot key does Ubuntu boot?

This says Ubuntu is first in boot list, but I do not understand why Windows is not shown?

>  BootOrder: 0000,3001,3002,3003,2001,2002
Boot0000* ubuntu    HD(2,c8800,82000,a76bd5d3-ac80-4d0d-89d5-fb10b4490040)File(EFIubuntugrubx64.efi)
Boot0001* Windows Boot Manager    HD(2,c8800,82000,a76bd5d3-ac80-4d0d-89d5-fb10b4490040)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot2001* USB Drive (UEFI)    RC



Boot-Repair sees all the efi files that HP put in the default efi partition, so it created boot entries for all of them. You probably can delete most of them by editing 25_custom. Details in link in my signature.

Grub used to have a bug where it did not create a UEFI boot entry. It looks like the one created is correct an dyou may not need any of the entries in 25_custom.

The files far from start of drive warning probably does not apply. I have yet to see a UEFI system need changes, It is more for some combination of BIOS settings, grub and maybe only external drives or USB driver.

I think it may be some HPs that only boot Windows, so if you cannot get it to boot Ubuntu, Boot-Repair can do a rename for those buggy UEFI that only boot Windows. It renames shim to be the Windows file so UEFI thinks it is booting Windows. Then from grub menu you can boot the backed up actual Windows file.

---


---
title: "Problem with bootloader after install"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by holoplex on 2012-10-17
Hi all,

I've tried several times today to install 12.10 server (x64) on a spare box using both the default and expert install, but seem to run up against the same problem.

When I reboot after completing the install I get this error on booting "Reboot and select proper boot device". I know this isn't a physical issue with the HDD as I've used the installation media to mount the filesystems and can indeed see all the files on the different partitions.

It seems as though the GRUB/EFI loader is installing to the wrong disk/partition. I'm installing from USB using unetbootin and it looks like the EFI partition is being written to USB (/dev/sdb) instead of the HDD (/dev/sda).

How can I sort out the bootloader? I'm not familiar with EFI, all my other (older) Linux installs have used standard grub2, with no EFI.

Thanks.

---

### Post by oldfred on 2012-10-17
Welcome to the forums.

I do not know servers, but one of the differences with UEFI is where grub is installed. With BIOS/MBR we always say to install to the MBR, never to a partition. But with UEFI the grub is installed to the efi partition which should be sda1. Then you have to boot with UEFI/BIOS and it should then boot ok.

If installing the server version you do not have a liveCD. But it may be good to have a liveCD to make repairs. Or download the full Boot-Repair CD.

Post the link to the BootInfo report. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by darkod on 2012-10-17
1. 12.10 is still in beta 2. It's not released yet. Is this only to test it? And even when it is released, most people would use and recommend only LTS for a server, which means 12.04 LTS. 12.10 will be a "normal" release, not LTS, which means much shorter support period.

2. To install for use with UEFI boot you need to boot the cd in UEFI mode to begin the installation, not in standard bios mode. Make sure you select correctly when booting the cd. On the other hand, if the board has the option to disable uefi (most of them do), it's better to disable it and use the standard bios boot.

---

### Post by holoplex on 2012-10-17
Thanks for the help guys, I solved the issues using [this thread]("http://ubuntuforums.org/showthread.php?t=1974392"), I have no need to use (U)EFI and that's what was causing the problem.

---


---
title: "Multi-boot with Windows7"
date: 2019-03-22
forum: Installation &amp; Upgrades
---

### Post by fra_pennaz on 2019-03-22
Dears,
I have a machine where I used to dual-boot windows&ubuntu. I recently formatted the ubuntu ext4 partition and installed ubuntu 18.04 from scratch. I admit I overlooked "efi-uefi-mbr-legacy"... But the defaults used to be always fine, please forgive me.
Now ubuntu 18.04 boots fine but I don't see the grub prompt and I can't boot Windows, although gparted says its partitions are there.

I installed boot-repair, it says it re-installed grub (and it notices windows is there), but still no grub prompt at boot.
boot-repair output is there [http://paste.ubuntu.com/p/ycNtDQfCPy/](http://paste.ubuntu.com/p/ycNtDQfCPy/)
it also says "The boot files of [The OS now in use - Ubuntu 18.04.2 LTS] are far from  the start of the disk. Your BIOS may not detect them. You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]"; but the operation of creating a new partition is forbidden because I already have the maximum number possible of primary partition, and I am a bit afraid of deleting the /dev/sda1 NTFS  primary partition (1 GiB) at the beginning of the disk with the label "SYSTEM".

Please help a poor users who usually solves its problems by himself without bothering forum expert users!

---

### Post by yancek on 2019-03-22
> I overlooked "efi-uefi-mbr-legacy

First mistake.  You installed Ubuntu in UEFI mode and your windows is a Legacy install on an MBR (mdos) partitioned system.  Note in the boot repair output that you have no entry for windows in the grub.cfg menu.  Windows boot partition (sda1) should be marked as active and you have sda6 (efi partition) marked as active.  You can try using GParted on the Ubuntu install media to change the active partition to sda1 and from Ubuntu run:  sudo update-grub.  Watch the output to see if you get a windows entry and reboot to test,  If that fails, set sda2 (windows OS partition) as active and try again.  I'm not sure if either of these options will work but no harm done if they fail.

If they fail, I think it would be simpler to re-install Ubuntu Legacy/MBR since that is what windows is.  I would suggest you read the link below, official Ubuntu documentation, at least the introduction and general principles section at the top and then scroll down to the section titled "Identifying if the computer boots the Ubuntu DVD in UEFI mode" so you know on boot if you are using Legacy or UEFI.  You must enable Legacy/CSM in the BIOS first.  Re-ionstall Ubuntu in Legacy mode and before doing that, delete sda6 which is the EFI partition and is not needed with a Legacy install.  The link below also explains this under the section at the bottom of the page "Conveting Ubuntu into Legacy Mode".

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)[h=2][/h]

---

### Post by oldfred on 2019-03-22
Generally best to always install systems in same boot mode.
Both Windows & Ubuntu install in the boot mode you use to boot install media. So always use UEFI or always use BIOS to boot installer.

You can only have one install in BIOS and another in UEFI with Windows in BIOS mode if on separate drives.
Windows requires boot flag on the primary NTFS partition with its boot files (your sda1). UEFI requires boot flag on the ESP - efi system partition (your sda6). And you can only have one boot flag per drive.
Also UEFI and BIOS are not compatible, so once you start booting in one mode, you cannot change. Or grub can only boot other installs in same boot mode.

Windows also requires gpt partitioning for UEFI boot and MBR partitioning for BIOS boot. Ubuntu will let you install in UEFI mode to MBR (maybe it should not), but UEFI highly recommends using gpt partitioning.
Windows has required vendors to install in UEFI/gpt for all new systems since Windows 8 when released in 2012. The Windows 7 installer was later updated to also offer UEFI install.

---

### Post by fra_pennaz on 2019-03-25
Dear Oldfred & Yancek,
problem solved, thank you!
What I did:
1. in the Ubuntu wiki Yancek linked I read the "Converting Ubuntu into Legacy mode" part. First point is
```
If Ubuntu is installed on a GPT disk (you can check it via the 'sudo parted -l' command), use [Gparted]("https://help.ubuntu.com/community/Gparted") to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk.
```
but the drive seems not to be GPT. Hence, I marked as /boot the /dev/sda1 partition and removed the flags from sda6
2. With boot-repair I re-installed GRUB, this time it installed grub in the mbr, i.e. ok with legacy boot
3. The command ```
[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
``` returned correctly "legacy mode"
4. Reboot and entered bios, disabled uefi boot
5. Reboot, grub is  there but no windows
6. boot-repair again, this time it detected windows too
7. reboot, ubuntu and windows are both selectable in grub!

Thank you!!!!

---


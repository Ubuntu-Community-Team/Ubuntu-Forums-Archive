---
title: "Boot-repair shows success but ubuntu doesnt boot"
date: 2018-12-02
forum: Installation &amp; Upgrades
---

### Post by dushyg on 2018-12-02
Hi All,

I got frustrated with update issues on windows 10 and decided to install ubuntu 18.04.1 LTS. 
I am a total newbie to ubuntu and during the first install I accidently chose the option to delete everything and install ubuntu.

Then I used testdisk and recovered the NTFS partition that had my data files on it.

I installed ubuntu using live-usb but it gave me installation errors.

Then I ran boot-repair which gave me the below advice :

```
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?


=================== Final advice in case of suggested repair


The boot files of [Ubuntu 18.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted

So I manually created a fat32 250 mb partition and ran boot repair utility while in live usb session.

Then I reinstalled ubuntu using the "Choose something else" option, but ubuntu still doesnt boot from hard disk. 

Even though the last few lines of boot repair are :

Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda4/EFI/ubuntu/shimx64.efi file!   -- HOW DO I DO THIS ? CAN SOME ONE PLEASE GIVE ME EXACT COMMANDS TO BE RUN FROM TERMINAL ?

I tried to use below command to add a boot entry :
sudo efibootmgr -c -d /dev/sda4 -p 4 -L ubuntu -l /dev/sda4/EFI/ubuntu/shimx64.efi 

This entry shows up in efibootmgr -v , but machine still doesnt boot. Next time when I boot from live usb, this entry is no longer there when I run efibootmgr -v.

Below  is extract from pastebin  [http://paste.ubuntu.com/p/Y6N7XgTTTq/](http://paste.ubuntu.com/p/Y6N7XgTTTq/)  created by latest boot repair execution  :

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1          4892672  297863167  292970496 139.7G 83 Linux
/dev/sda2        297865214 1924204543 1626339330 775.5G  f W95 Ext'd (LBA)
/dev/sda3           514048    4892671    4378624   2.1G 82 Linux swap / Solaris
/dev/sda4  *          2048     514047     512000   250M  b W95 FAT32
/dev/sda5        982343680 1871773695  889430016 424.1G  7 HPFS/NTFS/exFAT
/dev/sda6       1871775744 1924204543   52428800    25G  7 HPFS/NTFS/exFAT
/dev/sda7        297865216  982343679  684478464 326.4G 83 Linux

Partition table entries are not in disk order.




Disk /dev/sdb: 7.3 GiB, 7803174912 bytes, 15240576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x92e7cc21

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15240575 15238528  7.3G  c W95 FAT32 (LBA)



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda1, using the following options:        sda4/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file


```
```
/boot/efi added in sda1/fstab
Mount sda4 on /mnt/boot-sav/sda1/boot/efi
efi files in sda4/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi

*******lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05)
Subsystem: Lenovo Mullins [Radeon R4/R5 Graphics] [17aa:381a]
Kernel driver in use: radeon
Kernel modules: radeon, amdgpu
*******

grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.9,grub-install (GRUB) 2.

chroot /mnt/boot-sav/sda1 efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,2003,2002
Boot0000* EFI Network 0 for IPv4 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI Network 0 for IPv6 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* EFI USB Device (KingstonDataTraveler 109)    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x92e7cc21,0x800,0xe88580)RC
Boot0008* EFI Network 0 for IPv4 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0009* EFI Network 0 for IPv6 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

chroot /mnt/boot-sav/sda1 uname -r
Kernel: 4.15.0-29-generic

Reinstall the grub-efi-amd64-signed of sda1
Installing for x86_64-efi platform.
Primary GPT is invalid, using alternate GPT.
Primary GPT is invalid, using alternate GPT.
Primary GPT is invalid, using alternate GPT.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
efi files in sda4/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi
mkdir: cannot create directory ‘/mnt/boot-sav/sda5/efi’: Read-only file system
cp /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda5/efi/ubuntu/shimx64.efi
cp: cannot create regular file '/mnt/boot-sav/sda5/efi/ubuntu/shimx64.efi': No such file or directory
df /dev/sda4
Save and rename /mnt/boot-sav/sda1/boot/efi/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda1/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda1/boot/efi/EFI/Boot/bootx64.efi
efi files in sda4/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi /BOOT/bootx64.efi /BOOT/bkpbootx64.efi
Add /mnt/boot-sav/sda1/boot/efi efi entries in /mnt/boot-sav/sda1/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda1/boot/efi/EFI/BOOT/bkpbootx64.efi
Adding custom /mnt/boot-sav/sda1/boot/efi/EFI/BOOT/fbx64.efi
Adding custom /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/fwupx64.efi
Adding custom /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/mmx64.efi
mkdir: cannot create directory ‘/mnt/boot-sav/sda5/efi’: Read-only file system
df /dev/sda5
cp /mnt/boot-sav/sda1/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda5/efi/Boot/bootx64.efi (& .grb)
touch: cannot touch '/mnt/boot-sav/sda5/efi/Boot/bootx64.efi.grb': No such file or directory
Error no /mnt/boot-sav/sda5/efi/Boot/bootx64.efi.grb
Add /mnt/boot-sav/sda5 efi entries in /mnt/boot-sav/sda1/etc/grub.d/25_custom
Installing for x86_64-efi platform.
Primary GPT is invalid, using alternate GPT.
Primary GPT is invalid, using alternate GPT.
Primary GPT is invalid, using alternate GPT.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0

chroot /mnt/boot-sav/sda1 efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0003,2001,2003,2002
Boot0000* EFI Network 0 for IPv4 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI Network 0 for IPv6 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* EFI USB Device (KingstonDataTraveler 109)    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x92e7cc21,0x800,0xe88580)RC
Boot0003* ubuntu    HD(4,MBR,0x4461e7d1,0x800,0x7d000)/File(EFIubuntushimx64.efi)
Boot0008* EFI Network 0 for IPv4 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0009* EFI Network 0 for IPv6 (28-D2-44-FB-66-31)     PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(28d244fb6631,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

chroot /mnt/boot-sav/sda1 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda4/EFI/ubuntu/shimx64.efi file!
```

---

### Post by dushyg on 2018-12-02
Now following steps on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) to see if that helps

Latest pastebin url [http://paste.ubuntu.com/p/SWDMQDfhgS/](http://paste.ubuntu.com/p/SWDMQDfhgS/) still doesnt work after following steps on above bootpartition link.

---

### Post by vidtek on 2018-12-02
> **dushyg said:**
> Now following steps on [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) to see if that helps

Latest pastebin url [http://paste.ubuntu.com/p/SWDMQDfhgS/](http://paste.ubuntu.com/p/SWDMQDfhgS/) still doesnt work after following steps on above bootpartition link.

Looking at your system, it would seem at first glance to be ok.

Booting with UEFI is oldfred's  baby on here, he can help with most of your problems.

When all else fails, what I do is boot from the original install media, usb, dvd then:
```
sudo passwd root  #I change the temp root password to space or 1 just to make life easier
then su  and passwd.
```
Then do this:
```
mount /dev/sda4 /mnt  #this mounts your linux root partition
mount /dev/sda1 /mnt/boot/efi  # this mounts the boot partition
```
Then:```
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys    #  this binds the required files for a chroot session

chroot /mnt

```

Now you are in a chroot environment, you are acting directly on your linux system which is now active and working
```
grub-install /dev/sda  # it's always best to install grub to the actual device rather than a partition
update-grub  #   grub will complain about something missing-it's safe to ignore as it's a chroot session.
```

Then just cntrl-d to exit the chroot session.
Unmount the system:
```
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/proc
umount /mnt/sys
umount /mnt/boot/efi
umount /mnt
```

reboot and you should now have a grub menu at the start.

Cheers Tony.

---

### Post by oldfred on 2018-12-02
Please use code tags on longer text or terminal output. Also preserves formatting. Easy to add with Forum's advanced editor and # icon.
But with Boot-Repair better to just attach link to summary report.

Note that new systems have UEFI hardware, but you can install systems in UEFI or for backwards compatibility you can use CSM/legacy/BIOS mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives and only to gpt partitioned drives with UEFI.
You can install Ubuntu in either partitioning mode(MBR, gpt) and either boot mode (UEFI, BIOS). But with UEFI you really should use gpt as that is UEFI recommendation and gpt has improvements over the now 35 year old MBR partitioning.
Only if you really want Windows in BIOS boot mode should a drive be MBR, now. Also UEFI and BIOS are not compatible, or once you start booting in one mode you cannot switch. Or grub can only boot other installs in same boot mode.

Your drive is MBR partitioned.
And it is difficult to mix UEFI & BIOS on same drive with Windows.
Windows requires a primary MBR NTFS partition with boot flag on partition with its boot files.
But UEFI requires boot flag/esp flag on the FAT32 ESP - efi system partition. And only one boot flag per drive.
And you are not showing a primary NTFS partition for Windows to boot at all.

My suggestion is to backup all your data and do new installs both in UEFI mode to gpt partitioned drive. Converting to gpt on install will totally erase drive (or you may need to erase for Windows to see drive.)
How you boot install media UEFI or BIOS from UEFI boot menu is then how it installs. Since you have UEFI system, only boot in UEFI boot mode.
I would install Windows first, then Ubuntu.
For more info on Ubuntu install, see link in my signature.

---


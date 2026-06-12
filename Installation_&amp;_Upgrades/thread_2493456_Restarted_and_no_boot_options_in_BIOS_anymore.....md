---
title: "Restarted and no boot options in BIOS anymore...."
date: 2023-12-15
forum: Installation &amp; Upgrades
---

### Post by neptuneffs on 2023-12-15
Hi everyone,

Im not 100% sure this is the correct location to post this, but Im at my wits end.  Ive been running a dual boot Ubuntu/Windows 11 machine (they are installed on separate dedicated hard drives) for about a year with no problems whatsoever (windows is SOLELY for my SOLID works).  Today, my libre office crashed and I couldn't get it to reopen.  So I of course restarted the machine.  HUGE mistake. When it booted again, my computer booted straight to my UEFI BIOS utility where there are now NO options in the boot priority.  BOTH Ubuntu and Windows have vanished.

So I grabbed my Ubuntu install stick so that I could use the try Ubuntu option to run boot-repair.  The prints out is posted below.


Ive of course searched the terms there but have yet to come to a comprehensible answer...

What the heck is my path forward?  Is there anyway I can get back to booting properly with my two options without wiping my data?

Thank you!

Edit:
I've tried following [https://www.linuxbabe.com/desktop-linux/fix-cant-read-superblock-error](https://www.linuxbabe.com/desktop-linux/fix-cant-read-superblock-error) instructions, and tried an REISUB reboot.  The REISUB reboot sent me to a different boot screen, NOT directly into the BIOS
[https://imgur.com/a/txMRKuO](https://imgur.com/a/txMRKuO)

```
boot-repair readout.
boot-repair-4ppa2062                                              [COLOR=#666666][[/COLOR]20231215_1752[COLOR=#666666]][/COLOR]

[COLOR=#666666]=============================[/COLOR] Boot Repair [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]==============================[/COLOR]





/dev/sda [COLOR=#666666]([/COLOR]sda[COLOR=#666666])[/COLOR] has unknown type. Please report this message to [email]boot.repair@gmail.com[/email]
df: sda: No such file or directory
lsblk: sda: not a block device
/dev/sdb [COLOR=#666666]([/COLOR]sda[COLOR=#666666])[/COLOR] has unknown type. Please report this message to [email]boot.repair@gmail.com[/email]
df: sda: No such file or directory
lsblk: sda: not a block device
stat: cannot stat [COLOR=#BB4444]'sda'[/COLOR]: No such file or directory
sfdisk: cannot open sda: No such file or directory

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed: unhide-bootmenu-10s win-legacy-basic-fix


Quantity of real Windows: [COLOR=#666666]1[/COLOR]

Boot successfully repaired.

You can now reboot your computer.


[COLOR=#666666]============================[/COLOR] Boot Info After [COLOR=#B8860B]Repair[/COLOR] [COLOR=#666666]============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/nvme0n1.
 [COLOR=#666666]=[/COLOR]> Windows is installed in the MBR of /dev/nvme1n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/nvme0n1p2: can[COLOR=#BB4444]'t read superblock on /dev/nvme0n1p2.[/COLOR]

[COLOR=#BB4444]nvme1n1p1: _____________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       vfat[/COLOR]
[COLOR=#BB4444]    Boot sector type:  FAT32[/COLOR]
[COLOR=#BB4444]    Boot sector info:  No errors found in the Boot Parameter Block.[/COLOR]
[COLOR=#BB4444]    Operating System:  [/COLOR]
[COLOR=#BB4444]    Boot files:        [/COLOR]

[COLOR=#BB4444]nvme1n1p2: _____________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       [/COLOR]
[COLOR=#BB4444]    Boot sector type:  -[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]

[COLOR=#BB4444]nvme1n1p3: _____________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       ntfs[/COLOR]
[COLOR=#BB4444]    Boot sector type:  NTFS[/COLOR]
[COLOR=#BB4444]    Boot sector info:  No errors found in the Boot Parameter Block.[/COLOR]
[COLOR=#BB4444]    Operating System:  Windows 10 or 11[/COLOR]
[COLOR=#BB4444]    Boot files:        /Windows/System32/winload.exe[/COLOR]

[COLOR=#BB4444]sda: ___________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       ext4[/COLOR]
[COLOR=#BB4444]    Boot sector type:  -[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]
[COLOR=#BB4444]    Operating System:  [/COLOR]
[COLOR=#BB4444]    Boot files:        [/COLOR]

[COLOR=#BB4444]sdb: ___________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       ext4[/COLOR]
[COLOR=#BB4444]    Boot sector type:  -[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]
[COLOR=#BB4444]    Operating System:  [/COLOR]
[COLOR=#BB4444]    Boot files:        [/COLOR]

[COLOR=#BB4444]sdc: ___________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       iso9660[/COLOR]
[COLOR=#BB4444]    Boot sector type:  Unknown[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]
[COLOR=#BB4444]    Mounting failed:   mount: /mnt/BootInfo/FD/sdc: /dev/sdc already mounted or mount point busy.[/COLOR]


[COLOR=#BB4444]================================ 2 OS detected =================================[/COLOR]

[COLOR=#BB4444]OS#1:   Ubuntu 20.04.5 LTS on nvme0n1p2[/COLOR]
[COLOR=#BB4444]OS#2:   Windows 10 or 11 on nvme1n1p3[/COLOR]

[COLOR=#BB4444]================================ Host/Hardware =================================[/COLOR]

[COLOR=#BB4444]CPU architecture: 64-bit[/COLOR]
[COLOR=#BB4444]Video: Advanced Micro Devices, Inc. [AMD/ATI] from Advanced Micro Devices, Inc. [AMD/ATI][/COLOR]
[COLOR=#BB4444]Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)[/COLOR]

[COLOR=#BB4444]===================================== UEFI =====================================[/COLOR]

[COLOR=#BB4444]BIOS/UEFI firmware: 1410(14.10) from American Megatrends Inc.[/COLOR]
[COLOR=#BB4444]The firmware is EFI-compatible, and is set in EFI-mode for this live-session.[/COLOR]
[COLOR=#BB4444]SecureBoot disabled (confirmed by mokutil).[/COLOR]
[COLOR=#BB4444]BootCurrent: 0001[/COLOR]
[COLOR=#BB4444]Timeout: 1 seconds[/COLOR]
[COLOR=#BB4444]BootOrder: 0001,0002[/COLOR]
[COLOR=#BB4444]Boot0001* UEFI: Generic Flash Disk 8.07	PciRoot(0x0)/Pci(0x14,0x0)/USB(9,0)/CDROM(1,0x506fcc,0x7d00)..BO[/COLOR]
[COLOR=#BB4444]Boot0002* UEFI: Generic Flash Disk 8.07, Partition 2	PciRoot(0x0)/Pci(0x14,0x0)/USB(9,0)/HD(2,MBR,0x2cf4ba3a,0x506fcc,0x1f40)..BO[/COLOR]

[COLOR=#BB4444]a5e9b71b5ba86166bee504e1b254b7cf   nvme0n1p1/BOOT/fbx64.efi[/COLOR]
[COLOR=#BB4444]f75c300397e73f3fc7bfe46d49819bb2   nvme0n1p1/BOOT/mmx64.efi[/COLOR]
[COLOR=#BB4444]d4646b0af24b169d62bc44cff8967793   nvme0n1p1/ubuntu/grubx64.efi[/COLOR]
[COLOR=#BB4444]f75c300397e73f3fc7bfe46d49819bb2   nvme0n1p1/ubuntu/mmx64.efi[/COLOR]
[COLOR=#BB4444]64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi[/COLOR]
[COLOR=#BB4444]a84ccbe331b4a57c408ef9b4d34bea97   nvme0n1p1/Microsoft/Boot/bootmgfw.efi[/COLOR]
[COLOR=#BB4444]364c30b1bfed886aeda2947c02ee9072   nvme0n1p1/Microsoft/Boot/bootmgr.efi[/COLOR]
[COLOR=#BB4444]64349b3622c65f495a99dbf6102496e3   nvme0n1p1/BOOT/BOOTX64.efi[/COLOR]

[COLOR=#BB4444]============================= Drive/Partition Info =============================[/COLOR]

[COLOR=#BB4444]Disks info: ____________________________________________________________________[/COLOR]

[COLOR=#BB4444]nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes[/COLOR]
[COLOR=#BB4444]nvme1n1	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes[/COLOR]
[COLOR=#BB4444]sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes[/COLOR]

[COLOR=#BB4444]Partitions info (1/3): _________________________________________________________[/COLOR]

[COLOR=#BB4444]nvme0n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far[/COLOR]
[COLOR=#BB4444]nvme0n1p2	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB[/COLOR]
[COLOR=#BB4444]nvme1n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far[/COLOR]
[COLOR=#BB4444]nvme1n1p3	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB[/COLOR]
[COLOR=#BB4444]sda	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far[/COLOR]
[COLOR=#BB4444]sdb	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far[/COLOR]

[COLOR=#BB4444]Partitions info (2/3): _________________________________________________________[/COLOR]

[COLOR=#BB4444]nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]
[COLOR=#BB4444]nvme0n1p2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]
[COLOR=#BB4444]nvme1n1p1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]
[COLOR=#BB4444]nvme1n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]
[COLOR=#BB4444]sda	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]
[COLOR=#BB4444]sdb	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot[/COLOR]

[COLOR=#BB4444]Partitions info (3/3): _________________________________________________________[/COLOR]

[COLOR=#BB4444]nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1[/COLOR]
[COLOR=#BB4444]nvme0n1p2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1[/COLOR]
[COLOR=#BB4444]nvme1n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1[/COLOR]
[COLOR=#BB4444]nvme1n1p3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1[/COLOR]
[COLOR=#BB4444]sda	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda[/COLOR]
[COLOR=#BB4444]sdb	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda[/COLOR]

[COLOR=#BB4444]fdisk -l (filtered): ___________________________________________________________[/COLOR]

[COLOR=#BB4444]Disk nvme0n1: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors[/COLOR]
[COLOR=#BB4444]Disk identifier: F5B79781-25B6-462A-8A79-2E8D3799F4F2[/COLOR]
[COLOR=#BB4444]           Start        End    Sectors  Size Type[/COLOR]
[COLOR=#BB4444]nvme0n1p1    2048    1050623    1048576  512M EFI System[/COLOR]
[COLOR=#BB4444]nvme0n1p2 1050624 3907028991 3905978368  1.8T Linux filesystem[/COLOR]
[COLOR=#BB4444]Disk nvme1n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors[/COLOR]
[COLOR=#BB4444]Disk identifier: 78477881-71C3-414F-B60A-AFF33F95E9EE[/COLOR]
[COLOR=#BB4444]          Start        End    Sectors   Size Type[/COLOR]
[COLOR=#BB4444]nvme1n1p1   2048     206847     204800   100M Microsoft basic data[/COLOR]
[COLOR=#BB4444]nvme1n1p2 206848     239615      32768    16M Microsoft reserved[/COLOR]
[COLOR=#BB4444]nvme1n1p3 239616 1953523711 1953284096 931.4G Microsoft basic data[/COLOR]
[COLOR=#BB4444]Disk sdb: 7.28 TiB, 8001563222016 bytes, 15628053168 sectors[/COLOR]
[COLOR=#BB4444]Disk sda: 12.75 TiB, 14000519643136 bytes, 27344764928 sectors[/COLOR]
[COLOR=#BB4444]Disk sdc: 3.78 GiB, 4037017600 bytes, 7884800 sectors[/COLOR]
[COLOR=#BB4444]Disk identifier: 0x2cf4ba3a[/COLOR]
[COLOR=#BB4444]     Boot   Start     End Sectors  Size Id Type[/COLOR]
[COLOR=#BB4444]sdc1  *          0 5999871 5999872  2.9G  0 Empty[/COLOR]
[COLOR=#BB4444]sdc2       5271500 5279499    8000  3.9M ef EFI (FAT-12/16/32)[/COLOR]
[COLOR=#BB4444]sdc3       6000640 7884799 1884160  920M 83 Linux[/COLOR]

[COLOR=#BB4444]parted -lm (filtered): _________________________________________________________[/COLOR]

[COLOR=#BB4444]sda:14.0TB:scsi:512:4096:loop:ATA ST14000VN0008-2K:;[/COLOR]
[COLOR=#BB4444]1:0.00B:14.0TB:14.0TB:ext4::;[/COLOR]
[COLOR=#BB4444]sdb:8002GB:scsi:512:4096:loop:ATA ST8000NE001-2M71:;[/COLOR]
[COLOR=#BB4444]1:0.00B:8002GB:8002GB:ext4::;[/COLOR]
[COLOR=#BB4444]sdc:4037MB:scsi:512:512:unknown:Generic Flash Disk:;[/COLOR]
[COLOR=#BB4444]nvme0n1:2000GB:nvme:512:512:gpt:Samsung SSD 980 PRO 2TB:;[/COLOR]
[COLOR=#BB4444]1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;[/COLOR]
[COLOR=#BB4444]2:538MB:2000GB:2000GB:ext4::;[/COLOR]
[COLOR=#BB4444]nvme1n1:1000GB:nvme:512:512:gpt:Samsung SSD 980 PRO 1TB:;[/COLOR]
[COLOR=#BB4444]1:1049kB:106MB:105MB:fat32:windows:msftdata;[/COLOR]
[COLOR=#BB4444]2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;[/COLOR]
[COLOR=#BB4444]3:123MB:1000GB:1000GB:ntfs::msftdata;[/COLOR]

[COLOR=#BB4444]blkid (filtered): ______________________________________________________________[/COLOR]

[COLOR=#BB4444]NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL[/COLOR]
[COLOR=#BB4444]sda         ext4     2668806f-fa2d-49d8-8173-806a7b081448                                      large storage            [/COLOR]
[COLOR=#BB4444]sdb         ext4     de1c347b-268b-49bd-a563-669c90d85be8                                      small storage            [/COLOR]
[COLOR=#BB4444]sdc         iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 [/COLOR]
[COLOR=#BB4444]&#9500;&#9472;sdc1      iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 [/COLOR]
[COLOR=#BB4444]&#9500;&#9472;sdc2      vfat     54C5-9C6C                            2cf4ba3a-02                                                   [/COLOR]
[COLOR=#BB4444]&#9492;&#9472;sdc3      ext4     4bb46aa8-addf-480a-bc9a-d1e2c22b246f 2cf4ba3a-03                          writable                 [/COLOR]
[COLOR=#BB4444]nvme0n1                                                                                                                 [/COLOR]
[COLOR=#BB4444]&#9500;&#9472;nvme0n1p1 vfat     F614-F04D                            b517a78c-f8dd-4111-b573-b4b9f236c814                          EFI System Partition[/COLOR]
[COLOR=#BB4444]&#9492;&#9472;nvme0n1p2 ext4     f5606045-31ad-4a46-b342-0d4bb17726db 9010c450-1417-4879-8b26-c30f61eb8c33                          [/COLOR]
[COLOR=#BB4444]nvme1n1                                                                                                                 [/COLOR]
[COLOR=#BB4444]&#9500;&#9472;nvme1n1p1 vfat     661F-D998                            97611acc-3d07-44aa-9af9-41fa657df20f                          windows[/COLOR]
[COLOR=#BB4444]&#9500;&#9472;nvme1n1p2                                               3429e0b3-5599-4b12-9e4c-23c4f8a24089                          Microsoft reserved partition[/COLOR]
[COLOR=#BB4444]&#9492;&#9472;nvme1n1p3 ntfs     A40821760821489E                     554ffc3d-3663-4df8-aabe-293cf3769d3b                          Basic data partition[/COLOR]

[COLOR=#BB4444]Mount points (filtered): _______________________________________________________[/COLOR]

[COLOR=#BB4444]                                                               Avail Use% Mounted on[/COLOR]
[COLOR=#BB4444]/dev/nvme0n1p1                                                478.3M   6% /mnt/boot-sav/nvme0n1p1[/COLOR]
[COLOR=#BB4444]/dev/nvme1n1p1                                                   96M   0% /mnt/boot-sav/nvme1n1p1[/COLOR]
[COLOR=#BB4444]/dev/nvme1n1p3                                                834.5G  10% /mnt/boot-sav/nvme1n1p3[/COLOR]
[COLOR=#BB4444]/dev/sda                                                        5.3T  53% /mnt/boot-sav/sda[/COLOR]
[COLOR=#BB4444]/dev/sdb                                                        127G  93% /mnt/boot-sav/sdb[/COLOR]
[COLOR=#BB4444]/dev/sdc1                                                          0 100% /cdrom[/COLOR]

[COLOR=#BB4444]Mount options (filtered): ______________________________________________________[/COLOR]

[COLOR=#BB4444]/dev/nvme0n1p1                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro[/COLOR]
[COLOR=#BB4444]/dev/nvme1n1p1                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro[/COLOR]
[COLOR=#BB4444]/dev/nvme1n1p3                                                fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096[/COLOR]
[COLOR=#BB4444]/dev/sda                                                      ext4            rw,relatime[/COLOR]
[COLOR=#BB4444]/dev/sdb                                                      ext4            rw,relatime[/COLOR]
[COLOR=#BB4444]/dev/sdc1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048[/COLOR]

[COLOR=#BB4444]=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================[/COLOR]

[COLOR=#BB4444]search.fs_uuid f5606045-31ad-4a46-b342-0d4bb17726db root [/COLOR]
[COLOR=#BB4444]set prefix=($root)'[/COLOR]/boot/grub'
configfile [COLOR=#B8860B]$prefix[/COLOR]/grub.cfg

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc [COLOR=#666666]=========================[/COLOR]

Unknown BootLoader on sdc
```
[https://paste.ubuntu.com/p/rBCcV8TVXr/](https://paste.ubuntu.com/p/rBCcV8TVXr/)
[https://paste.ubuntu.com/p/SMfj3Cncrq/](https://paste.ubuntu.com/p/SMfj3Cncrq/)

---

### Post by oldfred on 2023-12-15
Are sda & sdb internal or external drives. One is not showing as gpt?
Report is not showing /etc/fstab in / on your install? Is that file really there or is report missing it?

Your nvme0n1p1 is showing as FAT32 but not ESP. It looks like it should have Windows boot files, but none shown?
You show no UEFI boot entries, neither Ubuntu nor Windows??
sudo efibootmgr -v

Either from Boot-Repair's advanced mode & its chroot to reinstall grub or chroot check for fstab and other issues:
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by neptuneffs on 2023-12-16
Thank you for taking the time to respond with a helpful comment!

To answer your questions:
sda&sdb are internal HDDs.  The sdc is the CD-ROM (DVD?, unsure the difference in the modern age).

"[COLOR=#000000]Your nvme0n1p1 is showing as FAT32 but not ESP. It looks like it should have Windows boot files, but none shown?[/COLOR]
[COLOR=#000000]You show no UEFI boot entries, neither Ubuntu nor Windows??"[/COLOR]
Indeed and that was the biggest shock to me when BOTH boot options disappeared from my BIOS simultaneously despite being on physically distinct SDDs.

I tried running sudo efibootmgr -v and it showed the generic flash disk. and that is it.  No windows, and no Ubuntu.

That said after running it I randomly tried repairing the superblock again and this time it worked!  so the drive is "mountable" and I can see the data; however, the GUI gnome filesystem shows some files and folders with giant red X's on them....Ill investigate that tomorrow, but efibootmgr made the superblock repairable!

I am going to look into the final three links you sent tomorrow (well later today), and will reply with more details.
[COLOR=#000000]


[/COLOR]

---

### Post by yancek on 2023-12-16
>  The REISUB reboot sent me to a different boot screen, NOT directly into the BIOS

That method as well as other reboot methods will not send the machine directly into the BIOS firmware as most machines will require a user to hit a specific key before accessing the BIOS.  Is that what you did?

Having some program like LibreOffice 'crash' should not have any effect on booting but the reason it crashed may.  Your EFI boot files are all on the Ubuntu drive, nvme0n1p1 .  The second partition on that drive shows an ext4 filesystem which would be Ubuntu.  That is unusual unless you installed windows after Ubuntu?

The UEFI output as indicated in the post above, shows only entries for USB flash drives and no entries for Ubuntu or windows which it should show.   It does detect both operating systems.  The lack of an /etc/fstab file is a major problem and I don't see how a crash of LibreOffice would cause that unless you were editing that file with Libre Office.  I'd start by trying the suggestions in the post above.

---

### Post by tea for one on 2023-12-16
As indicated by yancek, I, also, cannot reconcile that a LibreOffice crash would damage your UEFI boot menu.

Anyway, your screenshot [https://imgur.com/a/txMRKuO](https://imgur.com/a/txMRKuO) shows 4 disk drives recognised.
Samsung SSD 980 Pro 2TB
ST14000VN0008-2KU103
ST8000NE001-2M7101
Samsung SSD 980 Pro 1TB

More importantly, there is a warning about the Samsung SSD 980 Pro 2TB (your Ubuntu disk)
A failure may be imminent  - Backup and replace etc.

Now that you have repaired the superblock on this disk, can you see if you still have the warning?
This disk also contains your ESP, which has both Ubuntu and Microsoft boot files.

---

### Post by MAFoElffen on 2023-12-16
I'm either confused or that is in some very bad shape...

Do others see the same as I see there? I must just be tired.

I see the NVMe with problems in the ext4 filesystem in nvme0n1p2, where it says 20.04.5 is installed, but cannot mount it because it has a bad superblock. It says nvme0n1p1 is the ESP, with vfat, but can't read the EFI files there. It looks like that disk is Ubuntu (isolated install).

I see in nvme1n1p1 as vfat, but does not say it is ESP... But that NVMe drive looks like that NVMe is possibly Windows 10 (isolated install). But then still doesn't look completely right. Windows does not install without an ESP. An I looking at that wrong?

Then /dev/sda and /dev/sdb say they have ext4 filesystems, but no partitions(?). /dev/sda says it is not GPT, but doesn't say it is MS_DOS either... and is report as 14 TB. /dev/sdb is reported as 8TB... and I don't see a partition table on it(?)

No back ups right?

That can't be right. I must be confused. I must need to go back to sleep and relook at this when I wake up. Will think clearer in the morning.

---

### Post by neptuneffs on 2023-12-18
> **yancek said:**
> That method as well as other reboot methods will not send the machine directly into the BIOS firmware as most machines will require a user to hit a specific key before accessing the BIOS.  Is that what you did?

Having some program like LibreOffice 'crash' should not have any effect on booting but the reason it crashed may.  Your EFI boot files are all on the Ubuntu drive, nvme0n1p1 .  The second partition on that drive shows an ext4 filesystem which would be Ubuntu.  That is unusual unless you installed windows after Ubuntu?

The UEFI output as indicated in the post above, shows only entries for USB flash drives and no entries for Ubuntu or windows which it should show.   It does detect both operating systems.  The lack of an /etc/fstab file is a major problem and I don't see how a crash of LibreOffice would cause that unless you were editing that file with Libre Office.  I'd start by trying the suggestions in the post above.

With the REISUB reboot, it sends me to the screen telling me my hardrive may be dying backup immediately screen and I either have to push F1 as shown on the screen or simply reboot again and it will go straight to the BIOS.

So the specific sequence that happened is I was using LibreOffice to open a small csv file from a usb drive. Libre crashed, and nothing I could do could get it to restart. So on the advice on a different linux forum, I removed the usb stick and rebooted.  Big mistake apparently, but the root cause is still a mystery to me.

Yes, I installed Ubuntu first and was running quite happily for 6 months and even installed a play on linux virtual machine for running a few games I grew up playing and everything was just peachy until my windows only machine died.  Unfortunately SolidWorks NEEDS windows to operate so I then installed a copy of windows onto my machine.  As for why the names are shifted around I am not sure.  Honestly Ive never delved this deeply into file systems before...

Im trying the suggested steps and well, I'm encountering problems:

1) So the superblock fix works for ONE mount. After the unmounting, I get the same cannot read superblock error. And I get a whole host of errors when I am running the e2fsck:
Free block counts wrong
Free inodes count wrong
Directory counts wrong
Padding at the end of inode bitmap is not set.
Block bitmap differences: Group 0 block bitmap does not match checksum.
FIXED
Error writing file system infor: No data available

/dev/nvme0n1p2: ***** FILE SYSTEM WAS MODIFIED *****

2) The mounted SSD is read only, and it appears I cannot actually move the files anywhere.... Im testing with a fresh external HDD tomorrow and Ill report back!

3) When I try to follow the instructions [https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](https://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380) It works fine up to [COLOR=var(--black-600)][FONT=var(--ff-mono)]sudo mount /dev/sda1 /mnt/boot/efi where I get a sda1 does not exist error.  I try to proceed onwards and the grub install gives me the error "error: cannot find EFI directory"

4) I try to proceed to the second link: [/FONT][/COLOR]https://ubuntuforums.org/showthread.php?t=2349833&page=8&p=13602088#post13602088 and I get to the open step where I recieve an error "Device /dev/nvme0n1p2 is not a valid LUKS device"

5) I try to run fsck and I get
/dev/nvme0n1p2: recovering journal
fsck.ext4: Input/output error while recovering journal of /dev/nvme0n1p2
fsck.ext4: Unable to set superblock flags on /dev/nvme0n1p2

/dev/nvme0n1p2: ********** WARNING: Filesystem still has errors **********

---

### Post by neptuneffs on 2023-12-18
> **tea for one said:**
> As indicated by yancek, I, also, cannot reconcile that a LibreOffice crash would damage your UEFI boot menu.

Anyway, your screenshot [https://imgur.com/a/txMRKuO](https://imgur.com/a/txMRKuO) shows 4 disk drives recognised.
Samsung SSD 980 Pro 2TB
ST14000VN0008-2KU103
ST8000NE001-2M7101
Samsung SSD 980 Pro 1TB

More importantly, there is a warning about the Samsung SSD 980 Pro 2TB (your Ubuntu disk)
A failure may be imminent  - Backup and replace etc.

Now that you have repaired the superblock on this disk, can you see if you still have the warning?
This disk also contains your ESP, which has both Ubuntu and Microsoft boot files.

Well the specific sequence was Use LibreOffice to open a small csv file from a USB drive.  Program hangs. Cannot get it to open.  Remove the USB drive and reboot (as another linux forum suggested for LibreOffice problems opening csv files).  What cause this I have zero idea. it was most definitely NOT a power surge or physical damage in any way.  This is a software based issue, but I have no clue what it could be!

As for fixing the superblock, it lasts for exactly one mount and thus I will get the error screen as previously linked exactly once, thereafter it just goes straight to BIOS and the drive is totally unrecognized.  It appears that the e2fsck did NOT actually fix the issue with the superblock, merely slightly ameliorate it....


> **MAFoElffen said:**
> I'm either confused or that is in some very bad shape...

Do others see the same as I see there? I must just be tired.

I see the NVMe with problems in the ext4 filesystem in nvme0n1p2, where it says 20.04.5 is installed, but cannot mount it because it has a bad superblock. It says nvme0n1p1 is the ESP, with vfat, but can't read the EFI files there. It looks like that disk is Ubuntu (isolated install).

I see in nvme1n1p1 as vfat, but does not say it is ESP... But that NVMe drive looks like that NVMe is possibly Windows 10 (isolated install). But then still doesn't look completely right. Windows does not install without an ESP. An I looking at that wrong?

Then /dev/sda and /dev/sdb say they have ext4 filesystems, but no partitions(?). /dev/sda says it is not GPT, but doesn't say it is MS_DOS either... and is report as 14 TB. /dev/sdb is reported as 8TB... and I don't see a partition table on it(?)

No back ups right?

That can't be right. I must be confused. I must need to go back to sleep and relook at this when I wake up. Will think clearer in the morning.

I see the exact same thing as ou and it makes even less sense to me!  I was under the impression Ubuntu was on my 2TB SSD(nvme0) and Windows on my 1TB SSD (nvme1) and they didnt overlap at all, but since I installed Windows after installing ubuntu, I am not sure of anything.  The 14TB and 8TB sda and sdb are HDDs for larger file storage, where the data is selectively pulled to the SSD for processing, and the processed data file is returned to the HDD for storage. 

No backups, but Im quickly approaching the point of just saying "screw it" buying a new SSD to replace nvme0 and reinstalling Ubuntu. Hopefully ill be able to recover whats on sda and sdb....

---

### Post by tea for one on 2023-12-18
> **neptuneffs said:**
> I was under the impression Ubuntu was on my 2TB SSD(nvme0) and Windows on my 1TB SSD (nvme1) and they didnt overlap at all, but since I installed Windows after installing ubuntu, I am not sure of anything.
The "overlap" is the [COLOR="#0000FF"]E[/COLOR]fi [COLOR="#0000FF"]S[/COLOR]ystem [COLOR="#0000FF"]P[/COLOR]artition on your Ubuntu disk.
When you installed Windows after Ubuntu, the Windows installer (correctly) found the existing ESP (nvme0n1p1) and put the Windows boot files there.
You have a partition nvme1n1p1 on your Windows disk and you may be able to copy the Windows boot files to this partition.
Worth a shot to see if Windows boots.

Each OS on a separate disk is ideal provided that each disk has its own ESP for independent operation.
Only have the target disk visible when installing (UEFI mode with GPT)

> **neptuneffs said:**
>  Hopefully ill be able to recover whats on sda and sdb....
These storage disks may be OK according to the boot report info (although the partition info is missing)
```
                                                               Avail Use% Mounted on
/dev/sda                                                        5.3T  53% /mnt/boot-sav/sda
/dev/sdb                                                        127G  93% /mnt/boot-sav/sdb
```

---

### Post by tea for one on 2023-12-18
More info about superblock repair [https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by neptuneffs on 2023-12-18
Hi, Thank you tea for one for the advice on installing!  I will try to move the files, but everything seems to be Read-Only....

I tried to follow those steps about the superblock repair but I encounter a LOT of different errors (but follow on steps work) until I try to mkdir and it tells me the system is Read Only.  Ive tried to mount it in RW mode but that gives me the error pointing to a bad superblock.  It seems like a chicken and the egg problem, I need to be able to read write to fix the corrupt superblock, but I cannot mount it in read write mode because of the corrupt superblock.... Is there a way to work around this?

Pics for the errors im getting: [https://imgur.com/a/2LDdZFl](https://imgur.com/a/2LDdZFl)

---

### Post by tea for one on 2023-12-19
> **neptuneffs said:**
>  I will try to move the files, but everything seems to be Read-Only.
You'll need elevated permissions (i.e sudo) to move the Microsoft boot files from nvme0n1p1 to nvme1n1p1.
You will also need to mark the ESP on nvme1n1p1 with boot and esp flags - gparted will do this.
> **neptuneffs said:**
> I tried to follow those steps about the superblock repair but I encounter a LOT of different errors (but follow on steps work) until I try to mkdir and it tells me the system is Read Only.  
I'm very rusty on superblock repair, I haven't had to use it for eons.
However, many of these tutorials often assume that you already have root privileges and omit to mention [COLOR="#0000FF"]sudo[/COLOR] followed by the command.
Also, from your image, you need to unmount the partition nvme0n1p2 before sudo fsck.

---


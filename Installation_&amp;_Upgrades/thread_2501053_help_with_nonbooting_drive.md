---
title: "help with nonbooting drive"
date: 2024-09-20
forum: Installation &amp; Upgrades
---

### Post by chadalan on 2024-09-20
have a single 160gb ssd in my system. unfortunately for me, that drive is no longer booting. on attempted normal boot the pc simply says no bootable devices found. but, if i run from the live CD(usb stick), i can see the ssd drive is there and all the data appears to be on it; again, just can't boot from it any longer.

installed the boot repair app and sent to pastebin; which bring me to all of you via this post! can anyone please review and let me know what commands need run to repair the drive so that it boots again? thank you!!!!


below is my capture from: [https://paste.ubuntu.com/p/vzcvtNGvz9/](https://paste.ubuntu.com/p/vzcvtNGvz9/)


```


boot-repair-4ppa2081                                              [20240921_0203]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi




================================ 1 OS detected =================================


OS#1 (linux):   Ubuntu 24.04.1 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Oland [Radeon HD 8570 / R5 430 OEM / R7 240/340 / Radeon 520 OEM] HD Graphics 530 from Advanced Micro Devices, Inc. [AMD/ATI] Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04.1 LTS, noble, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.2.15(5.11) from Alienware
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0000,0002
Boot0000  Ubuntu	HD(1,GPT,388e9ac2-f865-49ca-9d33-5af897fe0e22,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi)
Boot0002  Ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* USB1 - EFI OS( USB DISK 3.0 PMAP)	PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/HD(1,MBR,0x82477cb6,0x800,0x39d17e0)0000424f


39bc76ff6662f4fbe9aa116e4c997b41   sda1/BOOT/fbx64.efi
4ba5a5aad43c197e9fb58b76b404d287   sda1/BOOT/mmx64.efi
66f69798ad23240e43b7ba0044a914c4   sda1/ubuntu/grubx64.efi
4ba5a5aad43c197e9fb58b76b404d287   sda1/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   sda1/ubuntu/shimx64.efi
07e25dcaf57c776875f78fa36827c58e   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB


Partitions info (2/3): _________________________________________________________


sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, vfat
sda2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 149.05 GiB, 160041885696 bytes, 312581808 sectors
Disk identifier: 098C5A14-BEAE-4098-B2FF-E813F3E9684A
       Start       End   Sectors  Size Type
sda1     2048   2203647   2201600    1G EFI System
sda2  2203648 312578047 310374400  148G Linux filesystem
Disk sdb: 28.91 GiB, 31042043904 bytes, 60628992 sectors
Disk identifier: 0x82477cb6
     Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 60628959 60626912 28.9G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:160GB:scsi:512:512:gpt:ATA INTEL SSDSA2BW16:;
1:1049kB:1128MB:1127MB:fat32::boot, esp;
2:1128MB:160GB:159GB:ext4::;
sdb:31.0GB:scsi:512:512:msdos: USB DISK 3.0:;
1:1049kB:31.0GB:31.0GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 vfat     6388-EFA9                            388e9ac2-f865-49ca-9d33-5af897fe0e22             
&#9492;&#9472;sda2 ext4     a28d2679-d90e-4ee8-99a7-4019e80e936e 1f79c6c4-147b-43fc-825d-9bded92b0791             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     C205-2591                            82477cb6-01                          UBUNTU 24_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda1                  1G   1% /mnt
/dev/sda2                  1G   1% /mnt
/dev/sda2              115.2G  15% /media/ubuntu/a28d2679-d90e-4ee8-99a7-4019e80e936e
/dev/sdb1               23.1G  20% /cdrom
efivarfs                    0  99% /sys/firmware/efi/efivars


Mount options (filtered): ______________________________________________________


/dev/sda1              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2              ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sda2              ext4            rw,relatime,errors=remount-ro
/dev/sdb1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid a28d2679-d90e-4ee8-99a7-4019e80e936e root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   a28d2679-d90e-4ee8-99a7-4019e80e936e
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/a28d2679-d90e-4ee8-99a7-4019e80e936e / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/6388-EFA9 /boot/efi vfat defaults 0 1
/swap.img	none	swap	sw	0	0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
   4.650436401 = 4.993368064    boot/grub/grub.cfg                             1
   3.181888580 = 3.416526848    boot/vmlinuz                                   2
  34.220958710 = 36.744474624   boot/vmlinuz-6.8.0-44-generic                  1
   3.181888580 = 3.416526848    boot/vmlinuz-6.8.0-45-generic                  2
  34.220958710 = 36.744474624   boot/vmlinuz.old                               1
 142.550777435 = 153.062731776  boot/initrd.img                                5
 141.572322845 = 152.012124160  boot/initrd.img-6.8.0-41-generic               1
 141.183589935 = 151.594725376  boot/initrd.img-6.8.0-44-generic               4
 142.550777435 = 153.062731776  boot/initrd.img-6.8.0-45-generic               5
 141.183589935 = 151.594725376  boot/initrd.img.old                            4


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the boot.


```

---

### Post by TheFu on 2024-09-20
Please edit the post above and wrap the report in forum code tags so the columns line up.  Make it easier for people to help you. There's a button for code-tags in the advanced editor.

---

### Post by yancek on 2024-09-21
Your drive (sda) shows as having a GPT drive and an EFI partition which is correct but if you scroll  about half way down the boot repair output you will see that sda2 where Ubuntu is installed has no fstab file which is necessary.  That should not happen if the install completed successfully.  You could try to manually create from using the usb but it would likely be much faster and easier to reinstall.  The necessary EFI file are on the partition.

---

### Post by ubfan1 on 2024-09-21
I see the /etc/fstab listed -- looks normal to me.

---

### Post by chadalan on 2024-09-21
thanks for the replies!!! they got me thinking of some more questions/ideas... the big one being: i have timeshift backup snapshots on an external drive!!  are there one or more files i could just copy from the backups to the nonbooting drive that will make it boot again?

---

### Post by oldfred on 2024-09-21
What brand/model system?
What video card/chip?

Can you boot to recovery mode in grub menu.
If one install, you have to press escape just after vendor UEFI/BIOS screen, but before grub menu normally appears.

---

### Post by TheFu on 2024-09-21
> **chadalan said:**
> thanks for the replies!!! they got me thinking of some more questions/ideas... the big one being: i have timeshift backup snapshots on an external drive!!  are there one or more files i could just copy from the backups to the nonbooting drive that will make it boot again?

Perhaps, perhaps not.  Was the timeshift created with the current OS?  If so, why didn't you already use that?  That's sorta the entire point of using timeshift. If so, I'd have used this within 15 minutes of any boot issue.  Why haven't you? Is there some reason that you should share for why you don't want to use it?

If timeshift was created for a different OS install, hard to say. Are the partitions EXACTLY the same? Are the file systems EXACTLY the same?  Not just the same size, but the same UUIDs, same LABELs, _EXACTLY_ the same.

---

### Post by yancek on 2024-09-21
> I see the /etc/fstab listed -- looks normal to me. 

I see that now at the bottom of the boot repair but also see 2 lines under partition info which indicate no fstab on sda2??

Since the OP implies that the system previous functioned properly so indicating what changes were made, if any just prior to this problem might help.  
 			  			   		 			 				 			 			 			 		 	 	 		 			 				 				 				 					[[IMG]https://ubuntuforums.org/clear.gif[/IMG] ]("https://ubuntuforums.org/newreply.php?do=newreply&p=14206323&noquote=1")

---

### Post by chadalan on 2024-09-21
sadly, i have never once in my life had an "actual" timeshift restore (meaning clicking the restore button in the app) work for me. [such attempts always result in boot failures (because, as mentioned, unless things are all _EXACTLY _the same on your system as what is in the backup, you will encounter issues.)] so, i just use timeshift as a "backup of files" and then pull the items i need like documents, config files, etc. (for example, i pull apache conf files frequently, web/vpn/ssh ssl keys, html/text/php docs, etc.)  so, that was my thinking: if someone can tell from the boot repair log what exactly is wrong/damaged/missing and if that issue can be resolved with replacing the damaged/missing file(s) maybe i can just grab those particular files from the timeshift snapshot and then use a live cd/usb of ubuntu to write them to the nonbooting drive.

---

### Post by chadalan on 2024-09-21
unfortunately, no idea why boot suddenly started failing. the system was stable. all i did was a simple reboot because i have teamviewer installed and it acts wonky on latest ubuntu. (but a reboot always clears up the issues temporarily as we wait for teamviewer company to actually fix the issues in a future release.)  so, all i could guess was maybe something that could have impacted the system/drive/boot process had updated in the background and when i rebooted that triggered the application of the update. (i do have ubuntu critical security patches set for autoinstall.) but, again, only a guess, it may have not been anything to do with updates at all.

---

### Post by tea for one on 2024-09-22
```
                       Avail Use% Mounted on
efivarfs                    0  99% /sys/firmware/efi/efivars
```
This detail is from line 129.
I had a quick internet search and there were many hits, some indicating a boot problem and others pointing to a variety of other events.
Anyway, there was a general opinion that the UEFI firmware should be reset to factory defaults.
It's worth a try because no extra harm should occur.
I would also suggest disabling Secure Boot & TPM (among other security settings)

---


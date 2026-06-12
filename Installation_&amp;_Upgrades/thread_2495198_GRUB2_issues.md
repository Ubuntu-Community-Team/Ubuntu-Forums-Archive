---
title: "GRUB2 issues"
date: 2024-02-11
forum: Installation &amp; Upgrades
---

### Post by kanukkountreh on 2024-02-11
Im trying to install ubuntu from live usb on my old gaming pc with a brand new 1tb drive. It looks like i got it installed ok but it will not boot to it. I can only get ubuntu to boot from live usb, but still get a error at the start saying grub_platform not found. then the grub menu comes up with only install or try , safe graphics .
[https://paste.ubuntu.com/p/2CPfW3VxtR/](https://paste.ubuntu.com/p/2CPfW3VxtR/)

I have tried most ideas i found, like reinstalling grub2 from live usb using mount and chroot etc, , m,

---

### Post by kanukkountreh on 2024-02-11
```
boot-repair-4ppa2075                                              [20240211_0517]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 23.10
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /etc/default/grub /grub/i386-pc/core.img 
                       /boot/grub/i386-pc/core.img

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.
       dmesg(1) may have more information after failed mount system call.


================================ 1 OS detected =================================

OS#1:   Ubuntu 23.10 on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: G86 [GeForce 8500 GT] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 23.10, mantic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: JOQ3510J.86A.0882.2008.0423.1925(0.0) from Intel Corp.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: DEC013D8-A591-4304-B2CB-0401E74E6691
     Start        End    Sectors   Size Type
sda1   2048       4095       2048     1M BIOS boot
sda2   4096 1953521663 1953517568 931.5G Linux filesystem
Disk sdb: 1.91 TiB, 2097152000000 bytes, 4096000000 sectors
Disk identifier: 2A585014-A55F-4771-AEF2-695C6F9E0059
        Start        End    Sectors  Size Type
sdb1        64   10094759   10094696  4.8G Microsoft basic data
sdb2  10094760   10104795      10036  4.9M EFI System
sdb3  10104796   10105395        600  300K Microsoft basic data
sdb4  10108928 4095997951 4085889024  1.9T Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000VM002-1ET1:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:1000GB:1000GB:ext4::;
sdb:2097GB:scsi:512:512:gpt:USB 3.0 USB 3.0:;
1:32.8kB:5169MB:5168MB::ISO9660:hidden, msftdata;
2:5169MB:5174MB:5138kB::Appended2:boot, esp;
3:5174MB:5174MB:307kB::Gap1:hidden, msftdata;
4:5176MB:2097GB:2092GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                PARTLABEL
sda                                                                                                            
&#9500;&#9472;sda1                                               a8e0a89e-9470-4305-b0e4-20981eb4261b                      
&#9492;&#9472;sda2 ext4     0cdc35c5-d004-4f9f-8783-bdd67779a43e d31d5478-91fc-4829-965a-a27a5f8401ec                      
sdb    iso9660  2023-10-16-11-29-57-00                                                    Ubuntu 23.10.1 amd64 
&#9500;&#9472;sdb1 iso9660  2023-10-16-11-29-57-00               2a585014-a55f-4771-aef3-695c6f9e0059 Ubuntu 23.10.1 amd64 ISO9660
&#9500;&#9472;sdb2 vfat     6F54-CACE                            2a585014-a55f-4771-aef0-695c6f9e0059 ESP                  Appended2
&#9500;&#9472;sdb3                                               2a585014-a55f-4771-aef1-695c6f9e0059                      Gap1
&#9492;&#9472;sdb4 ext4     1c8b711a-c2d8-11ee-a1a0-03ff6127bbec 474b8da0-ba61-42a2-ac69-5f247163236b writable             
sdc                                                                                                            
sdd                                                                                                            
sde                                                                                                            
sdf                                                                                                            

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/sda2                 860.7G   1% /mnt/boot-sav/sda2
/dev/sdb1                      0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda2                 ext4            rw,relatime
/dev/sdb1                 iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

======================== sda2/grub/grub.cfg (filtered) =========================

### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   0cdc35c5-d004-4f9f-8783-bdd67779a43e
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/0cdc35c5-d004-4f9f-8783-bdd67779a43e / ext4 defaults 0 1
/swap.img    none    swap    sw    0    0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 332.129264832 = 356.621082624  grub/grub.cfg                                  1
 552.143058777 = 592.859095040  boot/grub/grub.cfg                             1
 332.132358551 = 356.624404480  grub/i386-pc/core.img                          1
 552.141155243 = 592.857051136  boot/grub/i386-pc/core.img                     1
   3.608985901 = 3.875119104    boot/vmlinuz                                   1
   3.608985901 = 3.875119104    boot/vmlinuz-6.5.0-15-generic                  1
   3.608985901 = 3.875119104    boot/vmlinuz.old                               1
  20.140808105 = 21.626028032   boot/initrd.img                                2
  20.140808105 = 21.626028032   boot/initrd.img-6.5.0-15-generic               2
  20.140808105 = 21.626028032   boot/initrd.img.old                            2

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18228 Oct  2 14:23 10_linux
-rwxr-xr-x 1 root root 43202 Oct  2 14:23 10_linux_zfs
-rwxr-xr-x 1 root root 14459 Oct  2 14:23 20_linux_xen
-rwxr-xr-x 1 root root   786 Oct  2 14:23 25_bli
-rwxr-xr-x 1 root root 13120 Oct  2 14:23 30_os-prober
-rwxr-xr-x 1 root root  1174 Oct  2 14:23 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Sep  6 01:36 35_fwupd
-rwxr-xr-x 1 root root   214 Oct  2 14:23 40_custom
-rwxr-xr-x 1 root root   215 Oct  2 14:23 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda2 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Final advice in case of suggested repair: ______________________________________


The boot files of [sda2 (end>100GB)] are far from the start of the disk. 
Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). 
This can be performed via tools such as gParted. 
Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
 ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

---

### Post by kanukkountreh on 2024-02-11
im going to attempt boot repair utility after creating a 199mb boot partition at the front.

---

### Post by kanukkountreh on 2024-02-11
[https://paste.ubuntu.com/p/V9qCjTstzY/](https://paste.ubuntu.com/p/V9qCjTstzY/)

---

### Post by kanukkountreh on 2024-02-11
Didnt seem to work, i removed live usb (which was made using exact ubuntu instructions) and rebooted after boot repair completed (see 2nd paste link), I see the intel logo and press F2 for bios setup screen then it goes to a black screen with a flashing cursor in the top left corner like before and nothing happens for hours.

I put the live usb back in, rebooted, i see the word Grub in the top left corner where the cursor was flashing before for a few seconds, then i see a error grub_platform not found like before, but it still loads a basic grub menu with try/install, safe graphics and test memory. Which after waiting about half hour it loads into ubuntu from the live usb. (its a 2TB usb drive if it matters).

Im so at a loss, i'm a MCSE/CCNA but have only beginner experience with linux. Please help a newbie out.

There is no dual boot, no windows, and will be only single linux os. See the paste link for more detailed information. If anything else is needed, let me know. Ill check back tomorrow.

---

### Post by tea for one on 2024-02-11
> **kanukkountreh said:**
> Im trying to install ubuntu from live usb on my old gaming pc with a brand new 1tb drive. It looks like i got it installed ok but it will not boot to it. 
You could try an "old school" installation with only one partition (without a BIOS Boot partition):-
Remove all disks – only the target disk available
Boot into a “Try Ubuntu” live session in Legacy mode.
Open Gparted and create a msdos partition table on the target disk.
Open the installer
Installation type = Something else or Manual partitioning
Select free space and click the + sign
Create one Primary partition of 100GB with Ext4 file system and Mount point = / (system root)
Install bootloader to device not to a partition (e.g sda not sda1)
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP not found, ignore it and continue the installation.
The installer will show that only one partition is to be created and formatted.

It may work, it may not................?

Finally, given the age of your PC, perhaps Lubuntu or Xubuntu may be worth a shot.
(Lubuntu uses a different installer)

---

### Post by oldfred on 2024-02-11
You have mixed UEFI boot for Windows with BIOS boot for Ubuntu.
So default boot mode set in UEFI may be wrong depending on which system you are trying to boot.

Since UEFI system with UEFI Windows better to install Ubuntu in UEFI boot mode.
How you install UEFI or BIOS is based on which boot entry you use for the live installer. It should have two options, one clearly UEFI and one that just shows name or label of install flash drive.

Do not confuse a /boot partition which must be Linux formatted and not required for most desktop installs with an ESP - efi system partition required for UEFI boot. The ESP must be FAT32 with boot,esp flags if using gparted to create it.

You show an older nVidia card. What CPU? I found when I put an old nVidia card in my somewhat newer system, the CPU had better, higher rated graphics than the nVidia card. Also simplifies install as you do not need to install nVidia driver from Ubuntu repository.

While we typically recommend default install of just / (root) and if UEFI the ESP for newer users, and that normally works well for dual boot or older smaller drives. Default of just / goes back many years.
One step up but adds a bit of configuration is a separate /home partition. You split drive into ESP, / & /home partitions. You keep / just for the system and /home for your configuration settings (normally hidden) and all your data. I used to suggest 25 or 30GB for /, but now Ubuntu uses snaps that take a lot of space. You may need 40 or 50 GB for / if you use a lot of snaps.

I do not allow snaps and prefer Kubuntu as it works on older system, but seems to have all the features I want. Its more of a mid-weight system.
If older system, or lightweight configuration, you may need this:
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by MAFoElffen on 2024-02-11
Stop first... Freeze. Confirm these questions first.

Your first boot-info report said you have(/had) Ubuntu 23.10 installed as BIOS legacy boot, with the Disk partitioned with a GPT partition table with /dev/sda1 as a 1MB bios_boot partition, and the second /dev/sda2 as your system partition, right?

What was the original install of this OS done with years ago?

Because the version of Grub2 I see there on yours is v1.99-2.0...  Ubuntu 23.10 should have been 2.12~rc1. 

There is some missing blanks needed in the background info before proceeding. Just saying.

That, and before proceeding further, the bios_boot partition should be only 1MB to 5MB in size. Depending on how you resized that, you blew out the contents of what was in it during a resize... What was there was not written on a filesystem. It is a block-by-block write. So when you set it up for an install or Grub2 reinstall, you zero the contents as blank. To move or resize it, it begins at the same 1 sector offset, and writes the blocks of data, usually with using 'dd'... The MBR points to sector 1 (location)... not to a specific file.

[s]EDIT: I just say oldfred's post where he saw you have a mixed OS install of various OS'es with differing boot methods. I defer to his recommendations.[/s]

---

### Post by tea for one on 2024-02-11
A bit of confusion in this thread.
The OP only has Ubuntu - Windows is not installed
Line 305 - 307: 1 OS detected  OS#1:   Ubuntu 23.10 on sda2

---

### Post by MAFoElffen on 2024-02-11
That is what "I thought"... LOL.

---

### Post by oldfred on 2024-02-11
Sorry, missed that sdb was small and live installer, saw Microsoft partitions & ESP which installer in either mode has.

Ignore most of Oldfred's post on UEFI. But would still like to know CPU or what brand/model system it is.

---

### Post by kanukkountreh on 2024-02-11
Thank you for the info, im going to try a complete from scratch install then try a diff flavour if the clean install doesnt work, i had first tried to install the LTS listed first on the desktop page then after issues booting i tried a erase and install of the newest version listed 2nd. So maybe a conflict arose during that process, there has never been windows on this drive, its brand new and pretty sure no UEFI just bios.

---

### Post by mikechant on 2024-02-12
> Which after waiting about half hour it loads into ubuntu from the live usb. (its a 2TB usb drive if it matters).

I noticed this. Is this a typo? Do you really mean a **2TB** USB stick? If so, how much did you pay? Or did you actually mean some sort of USB attached SSD, or some different capacity?

Products claiming to be 2TB USB sticks are typically fake. There are loads of them on Amazon, for example. They may appear to work for a while but they will actually have a much smaller capacity and will corrupt previous data when writing later data. Some "genuine" 2TB sticks have been claimed to be available in the last six months or so but I can't find any actual reviews so far, so I'm sceptical, and the major brands like SanDisk don't seem to do anything with this capacity.

If it's one of these fake USB sticks you're not going to get very far.

---


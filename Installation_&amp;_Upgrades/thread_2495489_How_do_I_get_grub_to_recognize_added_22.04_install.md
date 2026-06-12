---
title: "How do I get grub to recognize added 22.04 installation?"
date: 2024-02-20
forum: Installation &amp; Upgrades
---

### Post by deh6 on 2024-02-20
I had Unbuntu 14.04, 16.04, 20.04 and did an upgrade of the 20.04 to 22.04. The grub selection still showed 20.04, and the new 22.04 booted. However, the upgraded 22.04 had many problems such as Firefox not working, Wi-Fi adaptor not found, not seeing monitor, shutdown hanging. I fixed the Firefox problem. After much work I gave up on the Wi-Fi adaptor. I decided to do a fresh install of 22.04 in another partition. The install appeared successful, but grub is unchanged, showing only selections for 14, 16, 20. I've tried numerous approaches, and fortunately have not ruined anything. I need some direction what to do next.

[https://paste.ubuntu.com/p/mSqz726XHT/](https://paste.ubuntu.com/p/mSqz726XHT/)

Don

---

### Post by Bashing-om on 2024-02-20
deh6; Hello

Can you boot to 22.04 presently ?
Maybe a simple " sudo update-grub" will suffice.
How many installs of other OSes do you now have ? Whereas I am a firm believer in that there can be only one booter in charge of the booting process - I have my primary system in charge of what OS to boot - disabling 30_os-prober in all the secondary OSes. No chance then of recursion in the boot code :D

Might be good to show us what is installed:
```

sudo blkid
sudo fdisk -lu

```
We are talking a UEFI install of 22.04 -- AND booting in UEFI mode - Yes ?
then
```

sudo efibootmgr -v

```
to list the boot entries.
From here later - one will employ efibootmgr to remove unwanted entries.

[INDENT]gotta start somewhere
[/INDENT]

---

### Post by oldfred on 2024-02-20
The Paste you are looking for does not currently exist. 

Please post a working pastebin, if you want specific help.

---

### Post by yancek on 2024-02-21
Posting a proper link will be necessary as suggested.  Were you previous installs of the earlier versions of Ubuntu all Legacy installs?  Are they all on the same hard drive?  Many more questions most of which can be answered with a proper boot repair.

---

### Post by deh6 on 2024-02-21
I'm not sure if this is the correct way to use pastebin. The link works fine outside of the forum, but not inside.

There are currently four OSs: 14, 16, 22 (upgraded from 20), 22. grub boots into 14, 16, 20. It's been *many *years since I wrestled with grub. I now *vaguely* remember something about the boot goes to one of the OSs to get grub, so it is probably still going to partition that was 20.

```
boot-repair-4ppa2075                                              [20240220_1238]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.7 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdb has 0 
                       sectors.
    Operating System:  
    Boot files:        


================================ 4 OS detected =================================

OS#1:   The OS now in use - Ubuntu 22.04.4 LTS on sda7
OS#2:   Ubuntu 14.04.5 LTS on sda1
OS#3:   Ubuntu 22.04.3 LTS on sda10
OS#4:   Ubuntu 16.04.7 LTS on sda6

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 3rd Gen Core processor Graphics Controller from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-29-generic root=UUID=83302829-03e3-40f0-b563-95517a7ee8ed ro quiet splash
df -Th / : /dev/sda7      ext4   61G   23G   36G  39% /

===================================== UEFI =====================================

BIOS/UEFI firmware: Q400A.206 from American Megatrends Inc.
This installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda7    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda9    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda10    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sda8    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda6    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda9    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda10    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda8    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda9    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda10    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda8    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Thanks for the responses. There are currently four OSs: 14, 16, 22 (upgraded 20), and 22. grub currently boots into 14, 16, and 20 (i.e. upgraded 20).

I'm not sure how pastebin is supposed to be used. The link works outside the forum, but not here. Here is the copy to clip board of the link--

Disk identifier: 0x000492df
     Boot      Start        End    Sectors   Size Id Type
sda1             2048  716491331  716489284 341.6G 83 Linux
sda2        717543422 3907028991 3189485570   1.5T  5 Extended
sda3  *     716492800  717541375    1048576   512M ef EFI (FAT-12/16/32)
sda5       1431830528 1465147391   33316864  15.9G 82 Linux swap / Solaris
sda6        847693824 1431830527  584136704 278.5G 83 Linux
sda7        717543424  847691775  130148352  62.1G 83 Linux
sda8       1465149440 2182612991  717463552 342.1G 83 Linux
sda9       2182615040 2899415039  716800000 341.8G 83 Linux
sda10      2899417088 3907028991 1007611904 480.5G 83 Linux
Partition table entries are not in disk order.
Disk sdb: 1.54 MiB, 1613824 bytes, 3152 sectors

parted -lm (filtered): _________________________________________________________

sda:2000GB:scsi:512:4096:msdos:ATA CT2000MX500SSD1:;
1:1049kB:367GB:367GB:ext4::;
3:367GB:367GB:537MB:fat32::boot, esp;
2:367GB:2000GB:1633GB:::;
7:367GB:434GB:66.6GB:ext4::;
6:434GB:733GB:299GB:ext4::;
5:733GB:750GB:17.1GB:linux-swap(v1)::;
8:750GB:1117GB:367GB:ext4::;
9:1117GB:1485GB:367GB:ext4::;
10:1485GB:2000GB:516GB:ext4::;
sdb:1614kB:scsi:512:512:unknown:MBED microcontroller:;

blkid (filtered): ______________________________________________________________

NAME    FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                    
&#9500;&#9472;sda1  ext4     fc65a06a-0110-42ac-85a6-0fda805fe4fd 000492df-01                                      
&#9500;&#9472;sda2                                                000492df-02                                      
&#9500;&#9472;sda3  vfat     EDDB-6663                            000492df-03                                      
&#9500;&#9472;sda5  swap     04ddd9e8-49f2-433a-8498-fb08e9b4f006 000492df-05                                      
&#9500;&#9472;sda6  ext4     47bf1ee0-8a96-4305-adba-5c1d1c20ac75 000492df-06                                      
&#9500;&#9472;sda7  ext4     83302829-03e3-40f0-b563-95517a7ee8ed 000492df-07                                      
&#9500;&#9472;sda8  ext4     1b6d6dfd-4579-498a-9ef8-9ea247ea2292 000492df-08                                      
&#9500;&#9472;sda9  ext4     d13a50bd-5424-45d3-8e8a-3eff58d7331e 000492df-09                                      
&#9492;&#9472;sda10 ext4     745189cf-282d-4e8f-88ad-5ec6ab6d0afd 000492df-0a                                      
sdb     vfat     2702-1974                                                                 NODE_F446RE 

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda10             435.6G   3% /mnt/boot-sav/sda10
/dev/sda1                3.3G  94% /mnt/boot-sav/sda1
/dev/sda6               14.5G  90% /mnt/boot-sav/sda6
/dev/sda7               35.2G  37% /
/dev/sda8              319.4G   0% /mnt/boot-sav/sda8
/dev/sda9              319.1G   0% /mnt/boot-sav/sda9
/dev/sdb                 1.5M   1% /media/deh/NODE_F446RE1

Mount options (filtered): ______________________________________________________

/dev/sda10             ext4            rw,relatime
/dev/sda1              ext4            rw,relatime,stripe=32749
/dev/sda6              ext4            rw,relatime
/dev/sda7              ext4            rw,relatime,errors=remount-ro
/dev/sda8              ext4            rw,relatime
/dev/sda9              ext4            rw,relatime
/dev/sdb               vfat            rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   fc65a06a-0110-42ac-85a6-0fda805fe4fd
Ubuntu 16.04.6 LTS (16.04) (on sda6)   47bf1ee0-8a96-4305-adba-5c1d1c20ac75
Ubuntu 20.04 LTS (20.04) (on sda7)   83302829-03e3-40f0-b563-95517a7ee8ed
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda1/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fc65a06a-0110-42ac-85a6-0fda805fe4fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=04ddd9e8-49f2-433a-8498-fb08e9b4f006 none            swap    sw              0       0

======================= sda1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq acpi=force apm=power_off quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_INIT_TUNE="480 440 1"

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  59.020854950 = 63.373160448   boot/grub/grub.cfg                             1
  78.751171112 = 84.558426112   boot/grub/i386-pc/core.img                     1
  57.065837860 = 61.273976832   boot/vmlinuz-3.13.0-106-generic                2
 177.455642700 = 190.541545472  boot/vmlinuz-3.13.0-107-generic                2
   0.466747284 = 0.501166080    boot/vmlinuz-3.5.0-54-generic                  2
 177.455642700 = 190.541545472  vmlinuz                                        2
  57.065837860 = 61.273976832   vmlinuz.old                                    2
  22.368160248 = 24.017629184   boot/initrd.img-3.13.0-106-generic             2
 191.018932343 = 205.105016832  boot/initrd.img-3.13.0-107-generic             3
  21.773815155 = 23.379456000   boot/initrd.img-3.5.0-54-generic               2
 191.018932343 = 205.105016832  initrd.img                                     3
  22.368160248 = 24.017629184   initrd.img.old                                 2

===================== sda1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 11608 Aug  2  2016 10_linux
-rwxr-xr-x 1 root root 10412 Aug  2  2016 20_linux_xen
-rwxr-xr-x 1 root root 11692 Aug  2  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Aug  2  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 22  2013 40_custom
-rwxr-xr-x 1 root root   216 Aug  2  2016 41_custom

====================== sda6/boot/grub/grub.cfg (filtered) ======================

Ubuntu   47bf1ee0-8a96-4305-adba-5c1d1c20ac75
Ubuntu 14.04.5 LTS (14.04) (on sda1)   fc65a06a-0110-42ac-85a6-0fda805fe4fd
Ubuntu 20.04.2 LTS (20.04) (on sda7)   83302829-03e3-40f0-b563-95517a7ee8ed
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda6/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=47bf1ee0-8a96-4305-adba-5c1d1c20ac75 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=04ddd9e8-49f2-433a-8498-fb08e9b4f006 none            swap    sw              0       0

======================= sda6/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda6: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 433.962352753 = 465.963528192  boot/grub/grub.cfg                             1
 619.377048492 = 665.051041792  boot/grub/i386-pc/core.img                     1
 673.156127930 = 722.795888640  boot/vmlinuz-4.4.0-178-generic                 1
 537.093643188 = 576.699908096  boot/vmlinuz-4.4.0-209-generic                 1
 523.874893188 = 562.506383360  boot/vmlinuz-4.4.0-210-generic                 1
 523.874893188 = 562.506383360  vmlinuz                                        1
 537.093643188 = 576.699908096  vmlinuz.old                                    1
 445.359996796 = 478.201655296  boot/initrd.img-4.4.0-178-generic              6
 537.344757080 = 576.969539584  boot/initrd.img-4.4.0-209-generic              3
 523.172847748 = 561.752567808  boot/initrd.img-4.4.0-210-generic              3
 523.172847748 = 561.752567808  initrd.img                                     3
 537.344757080 = 576.969539584  initrd.img.old                                 3

===================== sda6: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 12627 Aug 25  2020 10_linux
-rwxr-xr-x 1 root root 11082 Jun 17  2016 20_linux_xen
-rwxr-xr-x 1 root root 11692 Jun 17  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Jun 17  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 17  2016 40_custom
-rwxr-xr-x 1 root root   216 Jun 17  2016 41_custom

====================== sda7/boot/grub/grub.cfg (filtered) ======================

Ubuntu   83302829-03e3-40f0-b563-95517a7ee8ed
Ubuntu 14.04.5 LTS (14.04) (on sda1)   fc65a06a-0110-42ac-85a6-0fda805fe4fd
Ubuntu 16.04.7 LTS (16.04) (on sda6)   47bf1ee0-8a96-4305-adba-5c1d1c20ac75
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda7/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=83302829-03e3-40f0-b563-95517a7ee8ed /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=EDDB-6663  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda7/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda7: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 402.304542542 = 431.971213312  boot/grub/grub.cfg                             1
 374.927814484 = 402.575675392  boot/vmlinuz                                   1
 374.927814484 = 402.575675392  boot/vmlinuz-5.15.0-94-generic                 1
 402.990348816 = 432.707592192  boot/vmlinuz-5.4.0-29-generic                  1
 402.990348816 = 432.707592192  boot/vmlinuz.old                               1
 379.157905579 = 407.117701120  boot/initrd.img                                4
 379.157905579 = 407.117701120  boot/initrd.img-5.15.0-94-generic              4
 348.884101868 = 374.611451904  boot/initrd.img-5.4.0-29-generic               3
 348.884101868 = 374.611451904  boot/initrd.img.old                            3

===================== sda7: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Jul  2  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2020 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

===================== sda10/boot/grub/grub.cfg (filtered) ======================

Ubuntu   745189cf-282d-4e8f-88ad-5ec6ab6d0afd
Ubuntu 14.04.5 LTS (14.04) (on sda1)   fc65a06a-0110-42ac-85a6-0fda805fe4fd
Ubuntu 16.04.7 LTS (16.04) (on sda6)   47bf1ee0-8a96-4305-adba-5c1d1c20ac75
Ubuntu 22.04.4 LTS (22.04) (on sda7)   83302829-03e3-40f0-b563-95517a7ee8ed
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda10/etc/fstab (filtered) ==========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=745189cf-282d-4e8f-88ad-5ec6ab6d0afd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=EDDB-6663  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

====================== sda10/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

=================== sda10: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
1755.416057587 = 1884.863639552 boot/grub/grub.cfg                             1
1748.852115631 = 1877.815660544 boot/vmlinuz                                   1
1755.401363373 = 1884.847861760 boot/vmlinuz-6.2.0-26-generic                  2
1748.852115631 = 1877.815660544 boot/vmlinuz-6.5.0-18-generic                  1
1755.401363373 = 1884.847861760 boot/vmlinuz.old                               2
1792.177265167 = 1924.335685632 boot/initrd.img                                4
1792.042850494 = 1924.191358976 boot/initrd.img-6.2.0-26-generic               1
1792.177265167 = 1924.335685632 boot/initrd.img-6.5.0-18-generic               4
1792.042850494 = 1924.191358976 boot/initrd.img.old                            1

===================== sda10: ls -l /etc/grub.d/ (filtered) =====================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

===================== sda3/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 745189cf-282d-4e8f-88ad-5ec6ab6d0afd root hd0,msdos10 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda7,
using the following options:  sda3/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 22.04.4 LTS entry (sda3/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```

---

### Post by oldfred on 2024-02-21
Please use code Tags. Easy to use with Forum's Go Advanced editor & # icon.
But with Boot-Repair better to just attach link like you did in first post, but it needs to be a working link.

You show multiple installs, current as sda7.
And the install in sda7 is UEFI as fstab mounts the ESP.
But other installs & report are from BIOS boot.
Drive is also MBR(msdos), where UEFI is normally gpt. But conversion from MBR to gpt will totally erase drive, so only consider it if you have good backups & plan on new or totally erased drive.

To boot latest install make sure UEFI/BIOS is set to default boot in UEFI mode.
What brand/model system?

---

### Post by deh6 on 2024-02-21
oldfred,

I'm puzzled why the link I posted doesn't work when clicking on the link in the forum, but using the link in the browser brings it up just fine.

The system is an ASUS Q400A.

I looked in the firmware bios and I don't see anything that indicates a UEFI/BIOS. There was one item in the boot tab that suggested something different, but enabling it merely caused the boot to come back into the firmware setup.

The sda7 22.04 (which is the upgrade from 20.04) boots OK (though grub displays the selection as 20.04). I would stick with it, but there seems to be an inordinate amount of problems, so I thought a clean installation might work better. At one time I think there was an option in grub to boot to a specified partition; a sort of a manual way to get a boot started, but a lot has changed since then.

For the 22.04 in sda10, is there an option on the 22.04 installation that would avoid the UEFI issue? I didn't pay much attention when it was installing, as the progress seemed quite normal. I can run the install again and check. Time consuming stuff.

Doing something that erases the whole drive would be a disaster. Thanks for pointing that out! I have image backups, but it would be many days getting it restored. One reason for posting on the forum is to avoid wrecking the 14 and 16 OSs. Updating the external backup drive with 'dd' was about 1 1/2 days the last time I did it, and just before switching to a SSHD which is also bigger.

Earlier today, I tried running boot-repair from a live USB drive. It first cancelled because sda1 didn't have sufficient space. ('df' showed at 99%). I spent sometime cleaning out obsolete stuff, but the next attempt ended up cancelling, but it did get past the not sufficient free space check.

---

### Post by oldfred on 2024-02-21
Do you have latest UEFI/BIOS from Asus?  It may be newer, but still  older as they often stop updates after several years.

That is a third gen Intel, so would be UEFI or could be BIOS boot.

How you boot live installer UEFI or BIOS is then how it installs. Typically you have one entry that is clearly UEFI like UEFI : label and one that is just label which is the BIOS boot.  Label will be name or label of flash drive.

Using dd for backup is probably the worse way and dd's nickname is Data Destroyer as any typo totally destroys all data. Users often mis-type or do not realize that flash drive changed drive order, so wrong drive copied.

If taking more than about an hour to restore, your backup is not correct.
I now have SSD, so install is often 10-12 minutes, but with HDD it is only 15 min. Install to slow flash drives are the only ones that do take some time. Rsync restore of /home & data depends on amount of data, but usually quick. Even with fast Internet my download of the list of installed apps is longest. So total of about an hour to totally restore system. A few minor tweaks then as I go along may be required. 

Even with an UEFI install, you can add a BIOS boot stanza into a working BIOS grub. You just have to directly load a boot stanza into 40_custom.
I booted my Kubuntu UEFI install on external SSD that I use with my 1th Gen Intel, by adding a BIOS boot stanza to old HDD on 2006 BIOS only Intel dual core system. Actually that SSD made old system functional where before it barely worked. And it would not install Ubuntu and Kubuntu worked but was slow.

---

### Post by deh6 on 2024-02-22
oldfred,

Thanks for the comments.


[HTML]Do you have latest UEFI/BIOS from Asus?  It may be newer, but still  older as they often stop updates after several years.[/HTML]

I'll have to check. This machine is more than several years old. I may have done some updates when it was newer, but I don't remember. This current caper suggests that it may be time to get a new machine, though with the SSDHD and 16GB sram the speed is more than adequate.



[HTML]
Rsync restore of /home & data depends on amount of data, but usually quick. [/HTML]

I need to backup the OSs,  apps, and data. The 14.04 runs an old paid version of eagle CAD which doesn't run correctly on later 14.04 versions as well as everything later. It has the same problem on different computers, as well as other attempts such as VMWare with Windows, Linux, etc. Something about how the eagle did the display interface. So, with a live usb I 'dd' with compression the entire HD to an USB external drive.

Back to the grub problem. I revised the partitions and wiped out the 22.04 (on sd10 in the early drive parition layout). I did an install into a new partition of 20.04. Sometime back, I added 20.04 and grub updated OK, so I thought that maybe an installed of 20.04 might be different than 22.04. No difference. Grub still shows the original selections. The problem doesn't appear to be 22.04 specific.

For some reason it appears that something with grub doesn't get updated. "sudo os-prober" finds all the OSs correctly.

[[HTML]You just have to directly load a boot stanza into 40_custom
[/HTML]

I'll give that a try. I was looking at the earlier, but didn't pursue it. One issue is which OS installation is the one to modify 40_custom. At the moment it isn't clear where grub is picking up the .cfg.

---

### Post by yancek on 2024-02-22
Not sure what you've done, but if I understand correctly you installed 20.04 over the previous 22.04 which was on sda10.  The boot repair output shows Grub in the MBR on your Legacy machine pointing to the grub files on sda1 (14.04).  Your other installs were Legacy and you installed 22.04 in EFI mode on sda10 with an EFI partition sda3.  Grub in Legacy mode won't boot an EFI install on the same hard drive.  This was the problem.  If you installed 20.04 in EFI mode on that drive, your Grub from 14.04 won't boot it either.  If you have a setting to boot in EFI mode in the BIOS, you could then boot 20.04 you just installed on sda10 but you would not be able to boot the other Ubuntus as they are Legacy.  Grub in EFI mode won't boot a Legacy install on the same drive.  du

---

### Post by deh6 on 2024-02-22
It appears to be solved. The trick was to execute **'sudo update-grub' in the 14.04 OS (sda1).** Doing that from any of the other OSs, or a live USBs 22.04 or 20.04, did not change anything. (Bashing-om suggested doing 'sudo update-grub', but the key is doing it in the right OS.)

All the OSs now display in the grub selection menu and all boot correctly.

Surprising is that the key problems encounter with the 22.04 that was an upgrade from 20.04 disappeared as well. The Wi-Fi adaptor is seen and works, and the dual monitor arrangement also works. The monitor problem was clearly involved in the boot process, since booting with the monitor plugged in resulted in the laptop screen black/blank and the monitor working, but booting without the monitor resulted in the laptop screen working and the monitor was not seen when it was plugged in.

I don't quite understand the EFI and legacy mode issue. The firmware boot only has a CSM enable/disable, which I understand is a Compatibility Mode. If that setting was disabled, a boot simply returned to the firmware setup. Regarding EFI, I ran across a directory in /boot that was EFI, so I am wondering if that involves a workaround of the EFI|Legacy issue. 

Thanks for all the comments. It really helps, even if they don't provide the solution.

---


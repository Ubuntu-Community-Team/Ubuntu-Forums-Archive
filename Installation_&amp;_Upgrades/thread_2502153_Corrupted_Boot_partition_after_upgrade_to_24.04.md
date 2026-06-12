---
title: "Corrupted Boot partition after upgrade to 24.04"
date: 2024-11-03
forum: Installation &amp; Upgrades
---

### Post by wcalvert on 2024-11-03
Old user, new poster here looking for some expert advice on an issue with a Dual Boot ubuntu/windows Dell Inspiron system after upgrade to 24.04.

As for background, I did the upgrade from the online repository, and it's possible I selected an option to use the wrong boot configuration or something to that affect.  If I knew what I did, maybe there wouldn't be a problem, but alas, I'm getting old here!  Another similar system I upgraded worked fine, so some error on my part is the best guess going for now.  Wish I had more specifics.  The system is currently running in Live, and I do have a disk image of the corrupted drive on an external HD.

Now after the bad upgrade, the Gparted shows the EFI system partition and MIcrosoft reserved partition with errors (! mark in red).  I did run boot-repair and it gave specific instructions to ensure that the system should boot to sda1/efi/ubuntu/grubx64.efi, which it does, but that results in a boot to 24.04 with no access to any of my data.  Just like a clean new boot.

For EFI system:

"Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for fat32 file system support:  dosfstools, mtools."

For MS system:

"Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda2 is missing"

My impression is that a good way to proceed for a novice would be to use TestDisk in order to attempt a repair of the boot partitions.  If that worked, I could copy the repaired image back to my machine HD and press on.  This is probably obvious to you all, but the Live boot will not allow me in install TestDisk ... so here I am.

So the questions:

-  Can I boot my machine into the installed / damaged system, install TestDisk, then do the repair on the external disk?  

-  Are there better options for implementing my evil plan?

-  Am I on the wrong path?

If you need more info, I'd be happy to upload anything that might be helpful.  I did start this quest by making another post that didn't go far, but now I have new info and thought a fresh start might be wise.

I defer to the body, anyone have some wisdom to share? 

Cheers
Bill

---

### Post by oldfred on 2024-11-03
Microsoft reserved always shows errors as it is unformated. Gparted should check that type GUID is Microsoft reserved and not show as error.

Error on FAT32 may need chkdsk from Windows or dosfsck from Ubuntu. Partition must be unmounted or use live installer.

sudo /sbin/fsck.vfat -V <the fat32 device>
man dosfsck
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.
sudo fsck.vfat -t -a /dev/nvme0n1pY # where Y is ESP partition.

---

### Post by wcalvert on 2024-11-03
Thanks, will start reading and report back!

---

### Post by wcalvert on 2024-11-04
That was a quick failure.  You're way over my head on the format of the last two commands.  The first two returned:

ubuntu@ubuntu:~$ sudo /sbin/fsck.vfat -V /dev/sda
fsck.fat 4.2 (2021-01-31)
Logical sector size is zero.
ubuntu@ubuntu:~$ man dosfsck
ubuntu@ubuntu:~$ sudo fsck.vfat -t -a /dev/sda1
fsck.fat 4.2 (2021-01-31)
/dev/sda1: 311 files, 14695/126720 clusters

The last two returned errors.  Are you able to be more specific about the commands seeing what there is above?  Still reading [COLOR=Navy]UEFI boot install & repair info[/COLOR]

---

### Post by yancek on 2024-11-04
>   I did run boot-repair  

You forgot to post the link to the output as suggested on the boot repair home page.  That would be a good idea since you don't seem to be familiar with bootloaders.

>  that results in a boot to 24.04 with no access to any of my data

What data?  Data on another hard drive?  Another partition on the same drive?

The example command suggested by oldfred  (sudo fsck.vfat -t -a /dev/sda1) would do a filesystem check on an unmounted vfat partition that is on /dev/sda1 so if that is not your EFI partition, you need to change it to what your actual EFI partition is.

> The last two returned errors 

What two are you referring to?  The man dosfsck just opens the manual pages for that command.

---

### Post by oldfred on 2024-11-04
The examples were for those with HDD like sda or those with NVMe SSD type drives. 
You do not run a command like that on a drive like sda, but on a partition like sda2, but it must be the FAT32 partition.

You can confirm partitions, my flash drive often becomes sda & internal drive then is sdb.
sudo parted -l # that is a small el

---

### Post by grahammechanical on 2024-11-04
TestDisk does not repair partitions. It recovers or attempts to recover deleted files. You say this;

> and I do have a disk image of the corrupted drive on an external HD

If you want to experiment with TestDisk on the external HD then go ahead but that is a separate matter from the failure to boot after an online upgrade from Ubuntu 22.04 to 24.04. You also say this:

>  did run boot-repair and it gave specific instructions to ensure that  the system should boot to sda1/efi/ubuntu/grubx64.efi, which it does,  but that results in a boot to 24.04 with no access to any of my data.   Just like a clean new boot.

So, the booting problem is solved. 

Why is there no data there? This is again a separate matter. Are you sure that you did an online upgrade and not a fresh install which formatted the Ubuntu partition? Where was the Data? Was it on a separate partition or a separate drive? Or, in the Home folder and then in Documents; Downloads; Videos etc.? How are you trying to access the Data? 

The file manager (FILES) should be able to access that external HD. Open FILES - click Other Locations. What do you see there? You should see Ubuntu - that gives access to the OS you are using. You may also see other volumes that represent other partitions or drives. Click on them to mount them and then you can access them. You may be able to copy files to Ubuntu 24.04.

You can also do this from a TRY/LIVE ubuntu session also.

Regards

---

### Post by wcalvert on 2024-11-04
Ok, great replies, and yes as Yanek commented, I'm not familiar with boot loaders.  here's the boot-repair result:

```
boot-repair-4ppa2081                                              [20241030_1637]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/fwupdx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1 (linux):   Ubuntu 24.04.1 LTS on sda5
OS#2 (windows):   Windows 8 or 10 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: UHD Graphics 620 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.14.0(1.14) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,0000,0002
Boot0000* Windows Boot Manager    HD(1,GPT,d091f8d5-b26d-4623-87e5-6864351227bd,0x800,0xf9800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...r................
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)/HD(1,GPT,d091f8d5-b26d-4623-87e5-6864351227bd,0x800,0xf9800)/File(/EFI/Ubuntu)
Boot0002* UEFI: SanDisk Cruzer 8.02, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)..BO

66f69798ad23240e43b7ba0044a914c4   sda1/Boot/bkpbootx64.efi
66f69798ad23240e43b7ba0044a914c4   sda1/Boot/bootx64.efi
2895d47544fd587b26c7e29be1295c27   sda1/Boot/fbx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/Boot/mmx64.efi
b79608a8b4b6d20b9434d77fe1b85b3d   sda1/ubuntu/fwupdx64.efi
66f69798ad23240e43b7ba0044a914c4   sda1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/ubuntu/shimx64.efi
ee7c82a82dd0ce765ff8f9515d0dfb55   sda1/Microsoft/Boot/bootmgfw.efi
86c49eee6e6bf50ddfdd9c62f6ad9e84   sda1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
sda5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: E6263EE3-847B-4E08-9B2D-93BF846CD904
          Start        End   Sectors   Size Type
sda1        2048    1023999   1021952   499M EFI System
sda2     1024000    1286143    262144   128M Microsoft reserved
sda3     1286144  929718271 928432128 442.7G Microsoft basic data
sda4  1952600064 1953521663    921600   450M Windows recovery environment
sda5  1541400576 1952600063 411199488 196.1G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 3.76 GiB, 4022337024 bytes, 7856127 sectors
Disk identifier: 0x2cf4ba3a
     Boot   Start     End Sectors  Size Id Type
sdb1  *          0 5999871 5999872  2.9G  0 Empty
sdb2       5271500 5279499    8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 7856126 1855487  906M 83 Linux

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
1:1049kB:524MB:523MB:fat32:EFI system partition:boot, esp;
2:524MB:659MB:134MB::Microsoft reserved partition:msftres;
3:659MB:476GB:475GB:ntfs:Basic data partition:msftdata;
5:789GB:1000GB:211GB:ext4::;
4:1000GB:1000GB:472MB:ntfs::hidden, diag;
sdb:4022MB:scsi:512:512:unknown:SanDisk Cruzer:;

Free space >10MiB: ______________________________________________________________

sda: 453964MiB:752637MiB:298673MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     EEDC-1691                            d091f8d5-b26d-4623-87e5-6864351227bd ESP                      EFI system partition
&#9500;&#9472;sda2                                               c3f72f69-12fb-4823-998c-849c888d7b69                          Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     2E38DFD638DF9B63                     d9a742a6-ede8-4cce-878f-d55fe158adcc OS                       Basic data partition
&#9500;&#9472;sda4 ntfs     5C1219C81219A852                     f7cd1e6f-7072-427d-b3f7-d197956be9e5 WINRETOOLS               
&#9492;&#9472;sda5 ext4     2e8a4205-058b-44bc-810a-910260e478f3 e3141ef3-8bb9-4441-828a-3a5b6546202f                          
sdb    iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2 vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3 ext4     e8fbacfc-6eee-46bc-a286-eb39f31c3d19 2cf4ba3a-03                          writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/sda1                                                     436.5M  12% /mnt/boot-sav/sda1
/dev/sda3                                                     406.1G   8% /mnt/boot-sav/sda3
/dev/sda4                                                       103M  77% /mnt/boot-sav/sda4
/dev/sda5                                                     139.5G  23% /mnt/boot-sav/sda5
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2e8a4205-058b-44bc-810a-910260e478f3 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2e8a4205-058b-44bc-810a-910260e478f3
Windows Boot Manager (on sda1)   osprober-efi-EEDC-1691
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2e8a4205-058b-44bc-810a-910260e478f3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EEDC-1691  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 765.030693054 = 821.445451776  boot/grub/grub.cfg                             1
 854.425060272 = 917.431922688  boot/vmlinuz                                   2
 766.437652588 = 822.956163072  boot/vmlinuz-5.15.0-124-generic                2
 854.425060272 = 917.431922688  boot/vmlinuz-6.8.0-47-generic                  2
 766.437652588 = 822.956163072  boot/vmlinuz.old                               2
 859.747066498 = 923.146383360  boot/initrd.img                                6
 799.864253998 = 858.847703040  boot/initrd.img-5.15.0-124-generic             7
 859.747066498 = 923.146383360  boot/initrd.img-6.8.0-47-generic               6
 799.864253998 = 858.847703040  boot/initrd.img.old                            7

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda5,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04.1 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

---

### Post by wcalvert on 2024-11-04
Let me add another request that will demonstrate my lack on knowledge:

How can I quote your comment inline so I can reply in context?  I'm not a social media user or lover of typing, so this hindrance is frustrating.  I'm sure any teenage can show me this but ...  I read the FAQ, no joy.  I want to stay in the Ubuntu world but am losing the fight!!

Quoted portions of other posts can be put into a Quote box. 

  If you are using New Reply you can simply select the text you wish to  have within a code box and use the # button on the reply editing  toolbar. 

  If you are using Quick Reply you can still achieve the same result by typing [c*de] at the beginning and [/c*de] at the end.

Where is the "reply editing toolbar?

The third line makes less sense ...

---

### Post by wcalvert on 2024-11-04
Can anyone give me a quick tutorial so we can press on with the issue?  Thanks

---

### Post by wcalvert on 2024-11-04
[QUOTE=
code Why is there no data there? This is again a separate matter. Are you sure that you did an online upgrade and not a fresh install which formatted the Ubuntu partition? Where was the Data? Was it on a separate partition or a separate drive? Or, in the Home folder and then in Documents; Downloads; Videos etc.? How are you trying to access the Data? /code

The file manager (FILES) should be able to access that external HD. Open FILES - click Other Locations. What do you see there? You should see Ubuntu - that gives access to the OS you are using. You may also see other volumes that represent other partitions or drives. Click on them to mount them and then you can access them. You may be able to copy files to Ubuntu 24.04.

You can also do this from a TRY/LIVE ubuntu session also.

Regards[/QUOTE]

test

---

### Post by oldfred on 2024-11-04
Boot-Repair looks normal.
But no second drive other than USB flash drive shown?
Does UEFI/BIOS show you have another internal drive? Or is it another USB connected drive?
What brand/model system?

Easy to add code tags with Forum's Go Advanced edit & # icon.
I often use quick reply and quote icon and manually edit quote to code. But you need [] around quote or code.
Or manually type in:
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

---

### Post by wcalvert on 2024-11-04
```
Boot-Repair looks normal.
But no second drive other than USB flash drive shown?
Does UEFI/BIOS show you have another internal drive? Or is it another USB connected drive?
What brand/model system?
```


Right now it is only booting reliably in Live, so nothing else is showing.  When I try to get it boot "normally", it boots to a login screen that ends in a black screen with a command line.  When it does boot to 24.04, it boots to dev/sda6 ... I don't know what that is, probably a later path that was added during the upgrade.  It always look like a fresh install, no access to any previous browsers, apps etc.  Also no access to documents, videos etc.

You ask if UEFI/BIOS shows another internal drive ... Gparted does, that's what I find easiest to use.  Files often does not even when Gparted is showing it.  pretty confusing

This is a Dell Inspiron 5270

---

### Post by wcalvert on 2024-11-04
The FORUM prohibited this post unless it was in two parts ... I think:


```
 Easy to add code tags with Forum's Go Advanced edit & # icon.
I often use quick reply and quote icon and manually edit quote to code. But you need [] around quote or code.
Or manually type in:
If using Quick Reply then [C*DE] at the beginning and [/C*DE] at the end.          
```

I feel like I'm asking a quantum physicist how to use a lever!  where is  this "Forum Go Advanced" you refer to?  Quote icon?  Adding a C*DE  command is clearly problematic when it's part of your discussion.
Sorry to be so dense but this forum is all new to me.  

Also, don't take this as snarky, but I'm not wanting to become a  programmer, just want my system back!  I would really like to be able to  let someone trusted into my system to have a quick look around.  I"m  sure the problem would be glaringly obvious to anyone with a clue!

Would a view of the partitions from Gparted be helpful?

Any simple ideas of how to begin a recovery effort?

Thanks

---

### Post by 1fallen on 2024-11-04
See my screenshot, it will show you what to look for.

---

### Post by ajgreeny on 2024-11-04
You misunderstood **code** and **quote** tags in you last two posts, though I'm afraid I'm not sure what you mean about 2 separate posts being needed so I can't help with that.

Use **code tags** when you are copying and pasting terminal output or a system text file (such as /etc/fstab) but use **quote tags** when copy/pasting other text eg, a previous post or part thereof.

---

### Post by grahammechanical on 2024-11-04
> When it does boot to 24.04, it boots to dev/sda6 ... I don't know what  that is, probably a later path that was added during the upgrade

There is no partition sda6. You must mean partition sda5. I have a suggestion. When it dows boot to Ubuntu 24.04 open a terminal and type

```
sudo update-grub
```

Watch the printout. Paste or type that printout here. When using the terminal we can copy by selecting the text and pressing Ctrl + Shift (hold them down) then press C. To paste in a post of this forum press Ctrl + v

Regards

---

### Post by yancek on 2024-11-04
>  it boots to a login screen that ends in a black screen with a command line.   

Are you able to enter/type anything at the command line?  What does it look like, is it a user type prompt similar to the example below?

```
user@user-HP-Pavilion$ 
```

>   it boots to dev/sda6 

How do you determine that if you cannot log in?  If you notice your boot repair output it shows partitions on /dev/sda from sda1 - sda5 meaning there is no /dev/sda6.

Gparted will show all drives and partitions attached while Files will only show mounted drive partitions.  Boot repair should have shown all drives/partitions so if you had the drive attached when you ran boot repair, it should have shown information on that drive.  You might post an image of GParted output showing the drive.

When you go into the BIOS, do you see any indication of the other drive?

---

### Post by wcalvert on 2024-11-04
[INDENT]                  See my screenshot, it will show you what to look for.
[/INDENT]
            
                                                                               [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG]


Sorry, but my page under "Reply to Thread" does not have that box.  ??

---

### Post by wcalvert on 2024-11-04
I'm booted in now via recovery mode to 24.04, once I select Resume it continues successfully.

I would like to post a screenshot of Gparted, but when I do it returns a message saying that there is a Security token missing and a list of other items.  As soon as I paste the screen shot I am unable thereafter to submit that post even after deleting the screen shot

---

### Post by wcalvert on 2024-11-04
BTW, the Go Advanced option has now appeared under Quick Reply.  Wasn't there a couple of minutes ago.  This is killing me

---

### Post by wcalvert on 2024-11-04
Here is the response to Grub update:

wilson@wilson-Inspiron-5770:~$ sudo update-grub
[sudo] password for wilson: 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-48-generic
Found initrd image: /boot/initrd.img-6.8.0-48-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 24.04.1 LTS (24.04) on /dev/sda5
Adding boot menu entry for UEFI Firmware Settings ...
done

---

### Post by 1fallen on 2024-11-04
> **wcalvert said:**
> [INDENT]                  See my screenshot, it will show you what to look for.
[/INDENT]
            
                                                                               [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG]


Sorry, but my page under "Reply to Thread" does not have that box.  ??

Under "Reply with Quote"

---

### Post by wcalvert on 2024-11-04
> Under "Reply with Quote"                 

Found it under quick reply, but that little problem solved.  Thanks

---

### Post by wcalvert on 2024-11-04
> You might post an image of GParted output showing the drive.

Now, how to paste a shot of Gparted without getting the "Security Token missing" message that prevents me from posting ... ?

Is there another way to link a screenshot?

---

### Post by wcalvert on 2024-11-04
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294472&stc=1[/IMG]

---

### Post by wcalvert on 2024-11-04
> You might post an image of GParted output showing the drive.

Ok, getting the hang here.  Found a place to upload a file vice pasting.  Fine.

Now you should see the sda6 partition I was referring to earlier.

More thoughts?

The only thing I haven't done is to try > it boots to dev/sda6 per Yaneks request, that requires a reboot.

---

### Post by grahammechanical on 2024-11-04
You have two installs of Ubuntu 24.04. Your update-grub output was done with Ubuntu 24.04 on sda6 and it also found Ubuntu 24.04 on sda5. You should be getting a Grub boot menu. If you are able consistently to boot into Ubuntu 24.04 (Linux image: /dev/boot/vmlinuz-6.8.0-48-generic) then do so. It should be at the top of the Grub boot menu listed simply as Ubuntu.

I am guessing that your problems are caused by booting into Ubuntu 24.04.1 LTS (24.04) on /dev/sda5. If your files are not on Ubuntu 24.04 on sda6 then they may be on Ubuntu 24.04 on sda5.

You should be able to access the operating system on sda5 from the operating system on sda6.

Regards

---

### Post by wcalvert on 2024-11-04
> it boots to dev/sda6                      

returns "it cannot be found"

Tried with SUDO and similar result... sudo and it not found

Like the command is not correct

---

### Post by wcalvert on 2024-11-04
> You have two installs of Ubuntu 24.04. Your update-grub output was done  with Ubuntu 24.04 on sda6 and it also found Ubuntu 24.04 on sda5. You  should be getting a Grub boot menu. If you are able to consistently to  boot into Ubuntu 20.04 (Linux image: /dev/boot/vmlinuz-6.8.0-48-generic)  then do so. It should be at the top of the Grub boot menu listed simply  as Ubuntu.

Great, that's the kind of answer I was hoping for!  Now to clarify, I am not able to boot in 20.04, it always ends up in 24.04.

Can you elaborate on "Grub boot menu"?  
> I am guessing that your problems are caused by booting into Ubuntu  24.04.1 LTS (24.04) on /dev/sda5. If your files are not on Ubuntu 24.04  on sda6 then they may be on Ubuntu 24.04 on sda5.

You should be able to access the operating system on sda5 from the operating system on sda6.

So now I do have an option to boot into "Ubuntu" vice the "Ubuntu 24" that I  created to attempt a fix.  I also see an option to boot into Windows  (which I don't want anymore).  Use F2 to enter setup and modify the boot  order?  Is that on the right track?  Please advise with as much obvious detail you can manage, I think you're on it!!

---

### Post by oldfred on 2024-11-04
In UEFI, you only get one Ubuntu entry.
And then from its grub menu you get all the other systems that it can find, if you have os-prober on.
It found two Ubuntu & one Windows.
Default boot will be last installed or with grub reinstalled.
Can you not boot second Ubuntu? Or > Found Ubuntu 24.04.1 LTS (24.04) on /dev/sda5


Little key icon in gparted shows you have that mounted or you have booted sda6's install.

---

### Post by grahammechanical on 2024-11-05
I mis-typed Ubuntu 20.04 when I meant Ubuntu 24.04. I have since edited that post to correct the error. I am 76 years old. I get tired and stressed. I mangle my sentences.

You have two installs of Ubuntu 24.04. I think that the "Ubuntu" at the top of the Grub boot menu is 24.04 on sda6. It seems that you can boot into that install without problems. Use that install of Ubuntu 24.04 and try to access your data files in Ubuntu 24.04 on sda5. To copy files from one Ubuntu to the other open another thread.

I am going to suggest some useful but unrelated advice. Whatever install of Ubuntu 24.04 you are in open System Settings (cog icon) >System>Users. You should see a circle with your user initials in it. Click on the pencil icon on the bottom right corner and pick a picture. That picture will then appear on the login screen of the install of Ubuntu 24.04 that you are booting. I have more than one install of Ubuntu and I use this method to recognise which Ubuntu I am about to log into.

Regards

---

### Post by grahammechanical on 2024-11-05
> I also see an option to boot into Windows  (which I don't want  anymore).  Use F2 to enter setup and modify the boot  order?  Is that on  the right track?  Please advise with as much obvious detail you can  manage, I think you're on it!!

One thing at a time. And different questions should be asked in different threads. Start a new thread for that question. Imagine having medical issues that you want to see a doctor about but you have to make an different appointment for each different medical issue. That is the way we like to do things on this forum. 

Regards

---

### Post by wcalvert on 2024-11-05
This is great advice.  I'll ask a few questions and do some more reading then feel like I can move ahead.  Thanks

> In UEFI, you only get one Ubuntu entry.
And then from its grub menu you get all the other systems that it can find, if you have os-prober on.

_Where do I find the os-prober option enable?_

> Default boot will be last installed or with grub reinstalled.
Can you not boot second Ubuntu? Or 

I did see that the warning on the boot partition went away after I ran the sudo update-grub command. progress

> Little key icon in gparted shows you have that mounted or you have booted sda6's install.         

I am only able to boot to sda6, so my question was about _how to change the boot path, or is that the wrong idea?_

> I am 76 years old. I get tired and stressed. I mangle my sentences.

Graham, I'm 10 years behind you and sympathies completely!!  But your insight is spot on

> Use that install of Ubuntu 24.04 and try to access your data files in  Ubuntu 24.04 on sda5. To copy files from one Ubuntu to the other open  another thread.

I will do that, and hopefully you two will be there as well to help in the effort.  _Is there an easy way to "try to access your data files on sda5?"  _

That's about enough questions for one reply, hopefully you can weed through it all.  Thanks again for the help

---

### Post by oldfred on 2024-11-05
Your os-prober must be on as it found Windows & second Ubuntu install.
cat /etc/default/grub

From your grub menu are you not able to boot this entry in menu?
> Found Ubuntu 24.04.1 LTS (24.04) on /dev/sda5

From file browser are you not able to click on the partition that is sda5?
It probably is shown as a very long UUID as that is default.
I always label partitions, particularly those I only mount sometimes, as I do not know my UUIDs. I am a bit older  than you youngsters. :) So need labels. I add labels with gparted, disks, or with terminal. then default mount is by label.

example from a lsblk -f in terminal:
```

[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -f [/COLOR]
NAME FSTYPE FSVER LABEL      UUID                            FSAVAIL FSUSE% MOUNTPOINTS
[/FONT]sda6    ext4   1.0   data-a     f9537995-8b44-4abb-b5fb-ec27023f57b2  164.8G    40% /media/fred/data-a
```

---

### Post by wcalvert on 2024-11-05
This is what I see after the lsblk command:

```
NAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
&#9500;&#9472;sda1
&#9474;    vfat   FAT32 ESP   EEDC-1691                                           
&#9500;&#9472;sda3
&#9474;    ntfs         OS    2E38DFD638DF9B63                                    
&#9500;&#9472;sda5
&#9474;    ext4   1.0         2e8a4205-058b-44bc-810a-910260e478f3                
&#9492;&#9472;sda6
     ext4   1.0         1aceb469-c683-41a0-81e3-ede8fe0ff4b4  261.1G     4% /
```

---

### Post by wcalvert on 2024-11-05
I did some experimenting in an attempt to get a boot on sda5 by changing the boot flags, using boot repair to point to sda5 using Live and then reinstalling Grub .. no change.  Will still boot to sda6, but the straight Ubuntu boot option (the repair I did) to sda5 takes me to the command line, so something might be broken in sda5.

Maybe that's a clue about sda5?

---

### Post by grahammechanical on 2024-11-05
I have been looking at the picture of GParted. It shows /dev/sda5 as having 44.51 GiB used out of 96.08 GiB. I am guessing that that used space is where your data files are. How to access it?

Try to boot into it from the Grub menu which should say something like

> Ubuntu 24.04.1 LTS (24.04) on /dev/sda5

Tell us what happens. Lets us know if you have two working Ubuntu 24.04 installs and which one you want to be your main Ubuntu 24.04 installation.

Regards

---

### Post by oldfred on 2024-11-05
Edited your post to use Code Tags & remove loops which are just your snap apps.
Please always use Code Tags, easy to add with Forum's Go Advanced editor and # icon or use quote & change to code.

What happens when you try these?
Both mount sda5 with file browser as your lsblk did not show sda5 mounted.
And boot from grub menu of install in sda5.

---

### Post by wcalvert on 2024-11-05
> Try to boot into it from the Grub menu which should say something like

I'm all for that idea ... can you give more specifics on how to "boot from the Grub menu"?

Sorry for being so thick!!

---

### Post by oldfred on 2024-11-05
When you start system, does not grub menu appear with the entries that os-prober shows it found as shown in your post #22?
And you scroll down to which ever grub entry you want to boot.

Several examples, but has fancy background images & colors.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

More examples, started on last page of a mega-thread.
[https://ubuntuforums.org/showthread.php?t=2076205&page=58](https://ubuntuforums.org/showthread.php?t=2076205&page=58)

---

### Post by wcalvert on 2024-11-06
Ok, finally getting back to this fun!  I ran a script from the thread OldFred suggested and see this:

```
sudo] password for wilson: 
     0    Ubuntu
     1    Advanced options for Ubuntu
     2    Ubuntu, with Linux 6.8.0-48-generic
     3    Ubuntu, with Linux 6.8.0-48-generic (recovery mode)
     4    memtest86+
     5    Memory test (memtest86+x64.efi, serial console)
     6    Ubuntu 24.04.1 LTS (24.04) (on /dev/sda5)
     7    Advanced options for Ubuntu 24.04.1 LTS (24.04) (on /dev/sda5)
     8    Ubuntu (on /dev/sda5)
     9    Ubuntu, with Linux 6.8.0-47-generic (on /dev/sda5)
    10    Ubuntu, with Linux 6.8.0-47-generic (recovery mode) (on /dev/sda5)
    11    Ubuntu, with Linux 5.15.0-124-generic (on /dev/sda5)
    12    Ubuntu, with Linux 5.15.0-124-generic (recovery mode) (on /dev/sda5)
    13    UEFI Firmware Settings

```

This a part of my confusion since I wasn't aware that sometimes I was booting one version and then another.  I'll dig in now and decide which one I like best and we'll proceed to a new thread to talk about moving files over (hopefully!)  Cheers

---

### Post by wcalvert on 2024-11-06
So I've decided that the various options result in:  a. boot to command line  b.  boot to Dell Support Assist page, then shutdown  c.  Ubuntu 24.04

I have tried recovery mode, sometimes that works, other times it goes to command line.  I've made a matrix to try and sort it out, but if you look at the code I posted there are a lot of choices.

In the end, it doesn't really matter to me which one I use, just as long as we can move the old data to the new system.  At that point, I would like to clean up this boot mess.

Anyone see anything in my boot list that looks interesting?

Thanks

---


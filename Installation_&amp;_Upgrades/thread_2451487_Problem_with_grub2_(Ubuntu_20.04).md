---
title: "Problem with grub2 (Ubuntu 20.04)"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by usamanaveed786 on 2020-10-05
Hello and thank you in advance to anyone who takes the time to read and/or help.

I have a dell Inspiron laptop with 500GB SSD(Windows 10 Installed) and 1TB HDD(Ubuntu 18.04 Installed). When I start my laptop, Ubuntu automatically boot up and everything was going fine. If I had to boot windows 10 I had to enter the boot manager and select "Windows Boot Manager" and I was happy to do that because I rarely use Windows 10. 

Yesterday I upgraded my Ubuntu 18.04 to 20.04 and it broke during the upgrade and I was logged out and when I tried to login an error occurred in grey background saying "Something went wrong". I started digging into the problem and somehow I managed to upgrade my Ubuntu using tty4 terminal and rebooted my system. Now whenever I turn on my laptop grub window comes up with a list including "ubuntu". When I select ubuntu from the list it opens a new with with error message "error: you need to load the kernel first" and at the end it says "press any key to continue" and when I press any key it takes me back to the same grub window and this cycle continues.

I tried repairing grub by using boot-repair tool but nothing changed.

The only way I can boot into Ubuntu is by restarting my PC several times by pressing ctrl + alt + del. After restarting two to three times when I press "ubuntu" in grub list it boots. I have no idea why grub is behaving like this.

These are the content of boot-repair:

[HR][/HR]```
boot-repair-4ppa125                                              [20201005_1610]

============================= Boot Repair Summary ==============================




Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda2/fstab
sda2/boot/efi not empty

Unhide GRUB boot menu in sda2/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda2 ==================

grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.4

efibootmgr -v from chroot before grub install
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0000,0004
Boot0000* UEFI Hard Drive    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1024,32768,0)/HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(EFIBootBootX64.efi)N.....YM....R,Y.
Boot0001* ubuntu    HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0003* Windows Boot Manager    HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* UEFI ST1000LM049-2GH172 WN90LYVA    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)/HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(EFIBootBootX64.efi)N.....YM....R,Y.

uname -r
5.4.0-48-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi
cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Boot/

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v from chroot after grub install
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0000,0004
Boot0000* UEFI Hard Drive    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1024,32768,0)/HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(EFIBootBootX64.efi)N.....YM....R,Y.
Boot0001* ubuntu    HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0003* Windows Boot Manager    HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* UEFI ST1000LM049-2GH172 WN90LYVA    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)/HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(EFIBootBootX64.efi)N.....YM....R,Y.
Warning: NVram was not modified.

update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-48-generic
Found initrd image: /boot/initrd.img-5.4.0-48-generic
Found linux image: /boot/vmlinuz-5.4.0-47-generic
Found initrd image: /boot/initrd.img-5.4.0-47-generic
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 20.04.1 LTS CurrentSession entry (sda1/EFI/ubuntu/shimx64.efi file) !

============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


================================ 1 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.1 LTS CurrentSession on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-48-generic root=UUID=525e8d42-52d2-4b17-a8db-cd839b38ef8e ro quiet splash


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
No EFI in dmseg.
SecureBoot enabled.

efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0000,0004
Boot0000* UEFI Hard Drive    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1024,32768,0)/HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* ubuntu    HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Windows Boot Manager    HD(1,GPT,781a355c-43a6-4fee-b814-f1971d71be05,0x800,0x177000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* UEFI ST1000LM049-2GH172 WN90LYVA    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)/HD(1,GPT,fa4ea535-2e34-4a50-9f22-1e07578a448e,0x800,0x100000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.

2895d47544fd587b26c7e29be1295c27   sda1/BOOT/fbx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/BOOT/mmx64.efi
114bd85eec32e3162958ea034020821d   sda1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/ubuntu/shimx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: E7B2D43C-8526-490E-B3E0-32EBC04B1379
        Start        End    Sectors  Size Type
sda1     2048    1050623    1048576  512M EFI System
sda2  1050624 1953523711 1952473088  931G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM049-2GH1:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1000GB:1000GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 vfat     2F2A-02B6                            fa4ea535-2e34-4a50-9f22-1e07578a448e       EFI System Partition
&#9492;&#9472;sda2 ext4     525e8d42-52d2-4b17-a8db-cd839b38ef8e 92410db4-afce-47b4-9c20-32342248abb4       

df (filtered): _________________________________________________________________

                   Avail Use% Mounted on
sda2              747.9G  13% /

Mount options: __________________________________________________________________

sda2              rw,relatime,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 525e8d42-52d2-4b17-a8db-cd839b38ef8e root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   525e8d42-52d2-4b17-a8db-cd839b38ef8e
Ubuntu, with Linux 5.4.0-48-generic   525e8d42-52d2-4b17-a8db-cd839b38ef8e
Ubuntu, with Linux 5.4.0-47-generic   525e8d42-52d2-4b17-a8db-cd839b38ef8e
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=525e8d42-52d2-4b17-a8db-cd839b38ef8e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
/swapfile                                 none            swap    sw              0       0
UUID=2F2A-02B6  /boot/efi       vfat    defaults      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 168.695606232 = 181.135527936  boot/grub/grub.cfg                             1
 533.777477264 = 573.139202048  boot/vmlinuz                                   1
 533.707157135 = 573.063696384  boot/vmlinuz-5.4.0-47-generic                  1
 533.777477264 = 573.139202048  boot/vmlinuz-5.4.0-48-generic                  1
 533.707157135 = 573.063696384  boot/vmlinuz.old                               1
 533.777477264 = 573.139202048  vmlinuz                                        1
 533.707157135 = 573.063696384  vmlinuz.old                                    1
  37.336772919 = 40.090054656   boot/initrd.img                                3
 535.239253998 = 574.708772864  boot/initrd.img-5.4.0-47-generic               2
  37.336772919 = 40.090054656   boot/initrd.img-5.4.0-48-generic               3
 535.239253998 = 574.708772864  boot/initrd.img.old                            2
  37.336772919 = 40.090054656   initrd.img                                     3
 535.239253998 = 574.708772864  initrd.img.old                                 2

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 17622 Sep  8 13:24 10_linux
-rwxr-xr-x 1 root root 42359 Sep  8 13:24 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Sep  8 13:24 20_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 11  2019 30_os-prober
-rwxr-xr-x 1 root root  1424 Sep  8 13:24 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Nov 11  2019 40_custom
-rwxr-xr-x 1 root root   216 Nov 11  2019 41_custom
drwxr-xr-x 4 root root  4096 Oct  5 14:07 backup
```
[HR][/HR]Link to BootInfo summary: [https://paste.ubuntu.com/p/bBhdXZkpww/](https://paste.ubuntu.com/p/bBhdXZkpww/)

Any idea as to what I am doing wrong or if I am missing something?
I installed grub to /dev/sda but my ubuntu install is /dev/sda2 and I  got a warning not to do it to sda2 because it was an unreliable method.

I also mounted the disk after running boot-repair. Attached are the details of mounted disks. 

Any help will be greatly appreciated.

---

### Post by oldfred on 2020-10-05
Prefer you attach link Boot-Repair gives.

You are not showing SSD?
Have you updated UEFI from Dell and SSD firmware?

It shows UEFI Secure Boot on.
Windows updates and now fwupd in Linux may update UEFI. That often resets UEFI to defaults and may turn Secure Boot on, fast startup on, and maybe reset drives back to Intel RST. Double check all UEFI settings.
 I only can manually update UEFI but update whenever a new firmware is available, but have to keep a list of settings to redo.

---


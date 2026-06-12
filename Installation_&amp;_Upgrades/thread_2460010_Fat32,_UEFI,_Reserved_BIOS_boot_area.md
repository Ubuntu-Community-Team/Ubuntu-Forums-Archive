---
title: "Fat32, UEFI, Reserved BIOS boot area?"
date: 2021-03-31
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2021-03-31
I'm having Trouble installing Ubuntu on an HP ProBook 450 G3. The install just stalls halfway in.

I  edited Grub to be "quiet splash pci=noaer"

But I'm wondering about my partitions.
I have
/dev/sda2, ext4, root
/dev/sda3, ext4, home
But should
/dev/sda1, Fat32, be set to "reserved bios boot area"?

This UEFI messes me up on every clean install.

This is not a dual boot machine.

---

### Post by CatKiller on 2021-03-31
For a UEFI boot you need an [ESP](https://en.wikipedia.org/wiki/EFI_system_partition).

---

### Post by webmanoffesto on 2021-03-31
When I open GParted I can see that
/dev/sda1, Name: EFI, Fat32, flags: boot, esp
So why do my installs just stall?

The Lubuntu install told me that it successfully completed. But on reboot I get "BootDevice not found... Hard Disk - (3F0)

Then an Ubuntu install "successfully completed" and again "Boot Device Not Found"

---

### Post by CatKiller on 2021-03-31
> **webmanoffesto said:**
> So why do my installs just stall?

No idea.

Obviously if you're doing a UEFI install (which you should) you'll need to boot the machine (and install media) in UEFI mode rather than Legacy/CSM. And be using AHCI to access whatever drives you've got rather than onboard RAID.

---

### Post by oldfred on 2021-03-31
HP often wants to boot Windows by "Windows Boot Manager" only.

Can you boot ubuntu entry in UEFi boot menu, same place you booted USB flash drive.

Some with HP said updating UEFI and then only from within UEFI settings were they able to change boot order to have "ubuntu" entry first.
Linux & grub use efibootmgr to set boot order, but that only seems to work once with HP & maybe others with similar UEFI.
HP may be syncing Windows BCD & UEFI and that is why Boot-Repair suggests adding ubuntu entry into BCD, if dual booting.

Some only booting Ubuntu, have changed description of Ubuntu boot entry to use Windows description but boot using Ubuntu's shim/grub file. It checks description but not actual boot file.

Somewhere in link below in my signature is this with more alternatives.
D:  Use efibootmgr
    d1:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
   ```
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
```

Some also install rEFInd which is another boot manager.

Just for info, the ESP - efi system partition as FAT32 with boot,esp flags is for UEFI boot. That is where UEFI boot loaders put boot files & UEFI looks for those boot files.
The bios_grub partition is only for gpt partitioned drives booting in the old BIOS boot mode. BIOS boot looks for boot files in MBR. But MBR is tiny and with gpt, there is not any unused space after gpt's protective MBR for more boot code, so a 1MB unformatted partition with bios_grub flag is requried.

---

### Post by webmanoffesto on 2021-03-31
Okay, from boot menu I choose "UEFI - SanDisk Cruzer"

---

### Post by ActionParsnip on 2021-04-01
Is this to be a dual boot or is Ubuntu the only OS to be on the system? If it's a single boot then disable secure boot and make things easier

---

### Post by webmanoffesto on 2021-04-02
> **ActionParsnip said:**
> Is this to be a dual boot or is Ubuntu the only OS to be on the system? If it's a single boot then disable secure boot and make things easier

Single boot.
BIOS setup, System Configuration, is set to "Legacy Support Enable and Secure Boot Disable"

---

### Post by webmanoffesto on 2021-04-02
> **oldfred said:**
> HP often wants to boot Windows by "Windows Boot Manager" only.

This will be single boot, Ubuntu only.

---

### Post by webmanoffesto on 2021-04-02
> **oldfred said:**
> HP often wants to boot Windows by "Windows Boot Manager" only.
This is single boot, Ubuntu only. I was successfully doing that in the past. I don't know why I'm so stuck now. I think every time I have to do a fresh install on this laptop the UEFI messes me up. (But isn't that disabled on this now?)

When I go to Boot Menu, the first boot option is "UEFI - ubuntu", the 7th option is "Legacy - Samsung SSD". Is that good? or somehow a source of the problem?

Boot Repair Summary [http://paste.ubuntu.com/p/7HrHh9MJBc/](http://paste.ubuntu.com/p/7HrHh9MJBc/)
It said "Boot successfully repaired ... You can now reboot your computer ... Please do not forget to make your UEFI firmware boot on the Ubuntu 20 entry (sda1/EFI/ubuntu/shimx64.efi file)!"

```
boot-repair-4ppa129                                              [20210404_1553]

============================= Boot Repair Summary ==============================
/isodevice/boot/grub/menu.lst detected
/usr/share/boot-sav/bs-cmd_terminal.sh: line 177: warning: command substitution: ignored null byte in input

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file

/boot/efi added in sda2/fstab
sda2 is 100 % full
** Message: 15:53:57.447: x-terminal-emulator has very limited support, consider choose another terminal

** (pcmanfm:14865): WARNING **: 15:53:57.448: The directory '~/Templates' doesn't exist, ignoring it

(pcmanfm:14865): GLib-GIO-CRITICAL **: 15:53:57.632: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
The sda2 (Ubuntu 20.04.2 LTS) partition is still full. This can prevent to start it (e.g. you may get a Power Manager error).
Mount sda1 on /mnt/boot-sav/sda2/boot/efi

Unhide GRUB boot menu in sda2/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda2 ==================

grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.9

efibootmgr -v from chroot before grub install
BootCurrent: 000F
Timeout: 10 seconds
BootOrder: 0012,000F,000A,0010,000D,000E,000C,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,0011
Boot0000  Startup Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)....ISPH
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0003  3rd Party Option ROM Management    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0007  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0008  Boot Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0009  HP Recovery    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot000A* hp DVDRW DU8A6SH     PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)N.....YM....R,Y.....ISPH
Boot000C* Samsung SSD 850 EVO 1TB :     BBS(HD,Samsung SSD 850 EVO 1TB : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)......ISPH
Boot000D* hp DVDRW DU8A6SH :     BBS(CDROM,hp DVDRW DU8A6SH : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)......ISPH
Boot000E* Intel Corporation: Realtek PXE B02 D00    BBS(Network,Intel Corporation: Realtek PXE B02 D00,0x0)/PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)......ISPH
Boot000F* SanDisk Cruzer 4C530001091122106145    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)N.....YM....R,Y.....ISPH
Boot0010* SanDisk Cruzer 4C530001091122106145:     BBS(HD,SanDisk Cruzer 4C530001091122106145: ,0x900)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH
Boot0011  Network Boot    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0012* ubuntu    HD(1,GPT,4e2f7887-5652-4ed8-8691-2971382a9dc8,0x800,0x200000)/File(EFIubuntushimx64.efi)....ISPH

uname -r
5.3.0-28-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v from chroot after grub install
BootCurrent: 000F
Timeout: 10 seconds
BootOrder: 0012,000F,000A,0010,000D,000E,000C,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,0011
Boot0000  Startup Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)....ISPH
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0003  3rd Party Option ROM Management    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0007  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0008  Boot Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0009  HP Recovery    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot000A* hp DVDRW DU8A6SH     PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)N.....YM....R,Y.....ISPH
Boot000C* Samsung SSD 850 EVO 1TB :     BBS(HD,Samsung SSD 850 EVO 1TB : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)......ISPH
Boot000D* hp DVDRW DU8A6SH :     BBS(CDROM,hp DVDRW DU8A6SH : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)......ISPH
Boot000E* Intel Corporation: Realtek PXE B02 D00    BBS(Network,Intel Corporation: Realtek PXE B02 D00,0x0)/PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)......ISPH
Boot000F* SanDisk Cruzer 4C530001091122106145    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)N.....YM....R,Y.....ISPH
Boot0010* SanDisk Cruzer 4C530001091122106145:     BBS(HD,SanDisk Cruzer 4C530001091122106145: ,0x900)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH
Boot0011  Network Boot    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0012* ubuntu    HD(1,GPT,4e2f7887-5652-4ed8-8691-2971382a9dc8,0x800,0x200000)/File(EFIubuntushimx64.efi)

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-43-generic
Found initrd image: /boot/initrd.img-5.8.0-43-generic
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in sdb1/boot/grub/grub.cfg

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (sda1/EFI/ubuntu/shimx64.efi file) !

============================ Boot Info After Repair ============================

 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    31743936 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp fat part_msdos biosdisk
    ---------------------------------------------------------------------------

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
    Operating System:  Ubuntu 20.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04 20191223.............................................N....2....0............A20 gate n
    Boot sector info:  Syslinux looks at sector 5732480 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the 
                       /boot/syslinux directory. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/syslinux/syslinux.cfg /efi/BOOT/bootia32.efi 
                       /efi/BOOT/grubx64.efi /boot/grub/i386-pc/core.img 
                       /boot/syslinux/ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.2 LTS on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
No EFI in dmseg.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 000F
Timeout: 10 seconds
BootOrder: 0012,000F,000A,0010,000D,000E,000C,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,0011
Boot0000  Startup Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)....ISPH
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0003  3rd Party Option ROM Management    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0007  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0008  Boot Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0009  HP Recovery    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot000A* hp DVDRW DU8A6SH     PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)N.....YM....R,Y.....ISPH
Boot000C* Samsung SSD 850 EVO 1TB :     BBS(HD,Samsung SSD 850 EVO 1TB : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)......ISPH
Boot000D* hp DVDRW DU8A6SH :     BBS(CDROM,hp DVDRW DU8A6SH : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)......ISPH
Boot000E* Intel Corporation: Realtek PXE B02 D00    BBS(Network,Intel Corporation: Realtek PXE B02 D00,0x0)/PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)......ISPH
Boot000F* SanDisk Cruzer 4C530001091122106145    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)N.....YM....R,Y.....ISPH
Boot0010* SanDisk Cruzer 4C530001091122106145:     BBS(HD,SanDisk Cruzer 4C530001091122106145: ,0x900)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH
Boot0011  Network Boot    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0012* ubuntu    HD(1,GPT,4e2f7887-5652-4ed8-8691-2971382a9dc8,0x800,0x200000)/File(\EFI\ubuntu\shimx64.efi)....ISPH
This session has been detected as 'live' because /proc/cmdline contains (boot=casper)
This session has been detected as 'live' because df -Th / contains overlay

2895d47544fd587b26c7e29be1295c27   sda1/BOOT/fbx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/BOOT/mmx64.efi
957dc7e5f72c1d7393bf7850df5db2db   sda1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/ubuntu/shimx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/BOOT/BOOTX64.efi
1db7aa09c2bda1d08b0f7b61a54a2e2d   sdb1/BOOT/bootia32.efi
1bd54ad95660feab365d15299242ff9f   sdb1/BOOT/grubx64.efi
7095619324a9fb786422d7427c056405   sdb1/BOOT/BOOTx64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has---ESP,     liveusb,    not-mmc, no-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far
sda3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdb1    : not-sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sda2    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda3    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk identifier: 0x2c534026
        Boot Start     End Sectors  Size Id Type
loop0p1 *        0 1802239 1802240  880M  0 Empty
loop0p2        964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: D8457F12-33C1-4E11-89AD-EE4DF132E8CA
          Start        End    Sectors   Size Type
sda1       2048    2099199    2097152     1G EFI System
sda2    2099200  106956621  104857422    50G Linux filesystem
sda3  106956800 1953523711 1846566912 880.5G Linux filesystem
Disk sdb: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Disk identifier: 0x14fe293f
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 62529535 62527488 29.8G  b W95 FAT32
Disk zram0: 2 GiB, 2085203968 bytes, 509083 sectors
Disk zram1: 2 GiB, 2085203968 bytes, 509083 sectors
Disk zram2: 2 GiB, 2085203968 bytes, 509083 sectors
Disk zram3: 2 GiB, 2085203968 bytes, 509083 sectors

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:1075MB:1074MB:fat32:EFI:boot, esp;
2:1075MB:54.8GB:53.7GB:ext4:Root:;
3:54.8GB:1000GB:945GB:ext4:Home:;
sdb:32.0GB:scsi:512:512:msdos:SanDisk Cruzer:;
1:1049kB:32.0GB:32.0GB:fat32::boot;
zram3:2085MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2085MB:2085MB:linux-swap(v1)::;
zram1:2085MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2085MB:2085MB:linux-swap(v1)::;
zram2:2085MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2085MB:2085MB:linux-swap(v1)::;
zram0:2085MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2085MB:2085MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 vfat     EDAB-9E97                            4e2f7887-5652-4ed8-8691-2971382a9dc8                        EFI
&#9500;&#9472;sda2 ext4     f6de0803-7f04-4866-a0db-9253097ca5bc fd91393a-a5a1-478a-b4af-9f968e746dae                        Root
&#9492;&#9472;sda3 ext4     c26d322d-70c7-4737-bf81-4f0d0ed00da4 b4bb9d83-27ec-422b-8d5f-6b63c525796c Home                   Home
sdb                                                                                                              
&#9492;&#9472;sdb1 vfat     70AE-BE95                            14fe293f-01                          MULTISYSTEM            
zram0                                                                                                            
zram1                                                                                                            
zram2                                                                                                            
zram3                                                                                                            

df (filtered): _________________________________________________________________

        Avail Use% Mounted on
sda1   1011.3M   1% /mnt/boot-sav/sda1
sda2         0  95% /mnt/boot-sav/sda2
sda3    821.9G   0% /mnt/boot-sav/sda3
sdb1     24.7G  17% /isodevice

Mount options: __________________________________________________________________

sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2   rw,relatime
sda3   rw,relatime
sdb1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid f6de0803-7f04-4866-a0db-9253097ca5bc root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   f6de0803-7f04-4866-a0db-9253097ca5bc
Ubuntu, with Linux 5.8.0-43-generic   f6de0803-7f04-4866-a0db-9253097ca5bc
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=f6de0803-7f04-4866-a0db-9253097ca5bc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# /home was on /dev/sda3 during installation
UUID=c26d322d-70c7-4737-bf81-4f0d0ed00da4 /home           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0
UUID=EDAB-9E97  /boot/efi       vfat    defaults      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   1.000980377 = 1.074794496    boot/grub/grub.cfg                             1
   5.665035248 = 6.082785280    boot/vmlinuz                                   2
   5.665035248 = 6.082785280    boot/vmlinuz-5.8.0-43-generic                  2
  24.744766235 = 26.569490432   boot/initrd.img                                2
  24.744766235 = 26.569490432   boot/initrd.img-5.8.0-43-generic               2
  24.744766235 = 26.569490432   boot/initrd.img.old                            2

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 17622 Jan 13 14:12 10_linux
-rwxr-xr-x 1 root root 42359 Jan 13 14:12 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jan 13 14:12 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jan 13 14:12 30_os-prober
-rwxr-xr-x 1 root root  1424 Jan 13 14:12 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13 14:12 40_custom
-rwxr-xr-x 1 root root   216 Jan 13 14:12 41_custom

====================== sdb1/boot/grub/menu.lst (filtered) ======================

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.
timeout 30
default /default
#convert -resize 640x480 -colors 14 /media/multisystem/boot/splash/splash.png /media/multisystem/boot/splash/splash.xpm.gz
splashimage=/boot/splash/splash.xpm.gz
#color blue/green yellow/red white/magenta white/magenta
foreground=0033FF
background=FF3300
#http://diddy.boot-land.net/grub4dos/Grub4dos.htm
#http://www.boot-land.net/forums/index.php?showforum=66
#http://diddy.boot-land.net/grub4dos/files/syntax.htm
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_MENU_DEBUT|29-03-2021-23:22:30-005048439|ubcd538.iso|multisystem-ubcd|695Mio|
title ubcd538.iso
find --set-root /ubcd538.iso
map /ubcd538.iso (0xff) || map --mem /ubcd538.iso (0xff)
map --hook
chainloader (0xff)
boot
#MULTISYSTEM_MENU_FIN|29-03-2021-23:22:30-005048439|ubcd538.iso|multisystem-ubcd|695Mio|
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#http://diddy.boot-land.net/grub4dos/files/syntax.htm
title Chainloader into GRUB 2
find --set-root /boot/grub/boot.img
chainloader /boot/grub/boot.img
boot
#title Chainloader into Syslinux
#map (hd0) (hd0)
#map (hd0) (hd0)
#chainloader (hd0,0)+1
#rootnoverify (hd0,0)
##Autre solution pour chainer Syslinux
##faire une copie du mbr de la clé USB
##dd if=/dev/sd?1 of=/media/multisystem/syslinux.mbr bs=512 count=1
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#map (hd0) (hd0)
#map (hd0) (hd0)
#map --rehook
#find --set-root --ignore-floppies --ignore-cd /syslinux.mbr
#chainloader /syslinux.mbr
##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root /boot/syslinux/ldlinux.sys
#chainloader /boot/syslinux/ldlinux.sys
##Autre solution pour chainer Syslinux
#title Chainloader into Syslinux
#find --set-root --ignore-floppies --ignore-cd /boot/syslinux/redir.img
#kernel /boot/syslinux/memdisk
#initrd /boot/syslinux/redir.img
#http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/
title FreeDos
kernel /boot/syslinux/memdisk
initrd /boot/img/fdboot.img
title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2
title find and load BOOTMGR of Windows VISTA/SEVEN
fallback 2
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
savedefault --wait=2
title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies --ignore-cd /cmldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2
title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2
title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2
title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2
title find and boot ubcd.iso
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2
title commandline
commandline
title reboot
reboot
title halt
halt

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

ubuntu-20.04.2.0-desktop-amd64.iso
lubuntu-16.04.2-desktop-amd64.iso
boot-repair-disk-64bit.iso
______________Grub4Dos______________
Grub4Dos
______________Syslinux______________
Syslinux
Syslinux
Syslinux
______________UTIL______________
0-testfakebios
Windows 7 BIOS/MBR
Windows XP BIOS/MBR
grub.cfg auf sdb1
Chain other configfile
Return default menu
Chainer UUID de la partition
FreeBSD
TITLE
PLoP Boot Manager
Super Grub2 Disk
Super Grub Disk
Smart Boot Manager
BKO (boot.kernel.org)
vbeinfo
lspci
gfxpayload 640x480
gfxpayload 800x600
gfxpayload 1024x768
gfxpayload 1280x1024
Reboot

================== sdb1/boot/syslinux/syslinux.cfg (filtered) ==================

#http://www.syslinux.org/wiki/index.php?title=SYSLINUX#UI_module_options...
#default /boot/syslinux/vesamenu.c32
UI /boot/syslinux/vesamenu.c32
prompt 0
timeout 40
ontimeout 0
MENU TITLE MultiSystem LiveUSB
MENU DEFAULT 0
MENU BACKGROUND /boot/splash/splash.png
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
label 0
MENU LABEL PLoP Boot Manager
KERNEL /boot/img/plpbt
label 1
MENU LABEL Grub2
kernel /boot/syslinux/chain.c32 file=/boot/grub/boot.img
label 2
MENU LABEL Grub4Dos
kernel /boot/grub.exe
LABEL 3
MENU LABEL Hardware Detection Tool
KERNEL /boot/syslinux/hdt.c32
#Exemple pour booter un iso avec version recente de memdisk
#label 4
#MENU LABEL boot iso
#KERNEL /boot/syslinux/memdisk
#APPEND iso raw initrd=/g4u.iso
#LABEL 5
#KERNEL /boot/syslinux/memdisk
#APPEND initrd=freebsd.img floppy
#LABEL 6
#MENU LABEL Chainer win
#KERNEL /boot/syslinux/chain.c32 ntldr=/ntldr
#LABEL 7
#MENU LABEL Chainer partition 2
#kernel /boot/syslinux/chain.c32
#append hd0 2

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/menu.lst                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/grub/i386-pc/core.img                     1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/syslinux/syslinux.cfg                     1
            ?? = ??             boot/syslinux/ldlinux.sys                      1
            ?? = ??             boot/syslinux/cat.c32                          1
            ?? = ??             boot/syslinux/chain.c32                        1
            ?? = ??             boot/syslinux/cmd.c32                          1
            ?? = ??             boot/syslinux/cmenu.c32                        1
            ?? = ??             boot/syslinux/config.c32                       1
            ?? = ??             boot/syslinux/cptime.c32                       1
            ?? = ??             boot/syslinux/cpu.c32                          1
            ?? = ??             boot/syslinux/cpuid.c32                        1
            ?? = ??             boot/syslinux/cpuidtest.c32                    1
            ?? = ??             boot/syslinux/debug.c32                        1
            ?? = ??             boot/syslinux/dhcp.c32                         1
            ?? = ??             boot/syslinux/dir.c32                          1
            ?? = ??             boot/syslinux/disk.c32                         1
            ?? = ??             boot/syslinux/dmi.c32                          1
            ?? = ??             boot/syslinux/dmitest.c32                      1
            ?? = ??             boot/syslinux/elf.c32                          1
            ?? = ??             boot/syslinux/ethersel.c32                     1
            ?? = ??             boot/syslinux/gfxboot.c32                      1
            ?? = ??             boot/syslinux/gpxecmd.c32                      1
            ?? = ??             boot/syslinux/hdt.c32                          1
            ?? = ??             boot/syslinux/hexdump.c32                      1
            ?? = ??             boot/syslinux/host.c32                         1
            ?? = ??             boot/syslinux/ifcpu64.c32                      1
            ?? = ??             boot/syslinux/ifcpu.c32                        1
            ?? = ??             boot/syslinux/ifmemdsk.c32                     1
            ?? = ??             boot/syslinux/ifplop.c32                       1
            ?? = ??             boot/syslinux/kbdmap.c32                       1
            ?? = ??             boot/syslinux/kontron_wdt.c32                  1
            ?? = ??             boot/syslinux/ldlinux.c32                      1
            ?? = ??             boot/syslinux/lfs.c32                          1
            ?? = ??             boot/syslinux/libcom32.c32                     1
            ?? = ??             boot/syslinux/libgpl.c32                       1
            ?? = ??             boot/syslinux/liblua.c32                       1
            ?? = ??             boot/syslinux/libmenu.c32                      1
            ?? = ??             boot/syslinux/libutil.c32                      1
            ?? = ??             boot/syslinux/linux.c32                        1
            ?? = ??             boot/syslinux/ls.c32                           1
            ?? = ??             boot/syslinux/lua.c32                          1
            ?? = ??             boot/syslinux/mboot.c32                        1
            ?? = ??             boot/syslinux/meminfo.c32                      1
            ?? = ??             boot/syslinux/menu.c32                         1
            ?? = ??             boot/syslinux/pci.c32                          1
            ?? = ??             boot/syslinux/pcitest.c32                      1
            ?? = ??             boot/syslinux/pmload.c32                       1
            ?? = ??             boot/syslinux/poweroff.c32                     1
            ?? = ??             boot/syslinux/prdhcp.c32                       1
            ?? = ??             boot/syslinux/pwd.c32                          1
            ?? = ??             boot/syslinux/pxechn.c32                       1
            ?? = ??             boot/syslinux/reboot.c32                       1
            ?? = ??             boot/syslinux/rosh.c32                         1
            ?? = ??             boot/syslinux/sanboot.c32                      1
            ?? = ??             boot/syslinux/sdi.c32                          1
            ?? = ??             boot/syslinux/sysdump.c32                      1
            ?? = ??             boot/syslinux/syslinux.c32                     1
            ?? = ??             boot/syslinux/vesa.c32                         1
            ?? = ??             boot/syslinux/vesainfo.c32                     1
            ?? = ??             boot/syslinux/vesamenu.c32                     1
            ?? = ??             boot/syslinux/vpdtest.c32                      1
            ?? = ??             boot/syslinux/whichsys.c32                     1
            ?? = ??             boot/syslinux/zzjson.c32                       1

=============== sdb1: Version of COM32(R) files used by Syslinux ===============

 boot/syslinux/cat.c32              :  not a COM32/COM32R module
 boot/syslinux/chain.c32            :  not a COM32/COM32R module
 boot/syslinux/cmd.c32              :  not a COM32/COM32R module
 boot/syslinux/cmenu.c32            :  not a COM32/COM32R module
 boot/syslinux/config.c32           :  not a COM32/COM32R module
 boot/syslinux/cptime.c32           :  not a COM32/COM32R module
 boot/syslinux/cpu.c32              :  not a COM32/COM32R module
 boot/syslinux/cpuid.c32            :  not a COM32/COM32R module
 boot/syslinux/cpuidtest.c32        :  not a COM32/COM32R module
 boot/syslinux/debug.c32            :  not a COM32/COM32R module
 boot/syslinux/dhcp.c32             :  not a COM32/COM32R module
 boot/syslinux/dir.c32              :  not a COM32/COM32R module
 boot/syslinux/disk.c32             :  not a COM32/COM32R module
 boot/syslinux/dmi.c32              :  not a COM32/COM32R module
 boot/syslinux/dmitest.c32          :  not a COM32/COM32R module
 boot/syslinux/elf.c32              :  not a COM32/COM32R module
 boot/syslinux/ethersel.c32         :  not a COM32/COM32R module
 boot/syslinux/gfxboot.c32          :  not a COM32/COM32R module
 boot/syslinux/gpxecmd.c32          :  not a COM32/COM32R module
 boot/syslinux/hdt.c32              :  not a COM32/COM32R module
 boot/syslinux/hexdump.c32          :  not a COM32/COM32R module
 boot/syslinux/host.c32             :  not a COM32/COM32R module
 boot/syslinux/ifcpu64.c32          :  not a COM32/COM32R module
 boot/syslinux/ifcpu.c32            :  not a COM32/COM32R module
 boot/syslinux/ifmemdsk.c32         :  not a COM32/COM32R module
 boot/syslinux/ifplop.c32           :  not a COM32/COM32R module
 boot/syslinux/kbdmap.c32           :  not a COM32/COM32R module
 boot/syslinux/kontron_wdt.c32      :  not a COM32/COM32R module
 boot/syslinux/ldlinux.c32          :  not a COM32/COM32R module
 boot/syslinux/lfs.c32              :  not a COM32/COM32R module
 boot/syslinux/libcom32.c32         :  not a COM32/COM32R module
 boot/syslinux/libgpl.c32           :  not a COM32/COM32R module
 boot/syslinux/liblua.c32           :  not a COM32/COM32R module
 boot/syslinux/libmenu.c32          :  not a COM32/COM32R module
 boot/syslinux/libutil.c32          :  not a COM32/COM32R module
 boot/syslinux/linux.c32            :  not a COM32/COM32R module
 boot/syslinux/ls.c32               :  not a COM32/COM32R module
 boot/syslinux/lua.c32              :  not a COM32/COM32R module
 boot/syslinux/mboot.c32            :  not a COM32/COM32R module
 boot/syslinux/meminfo.c32          :  not a COM32/COM32R module
 boot/syslinux/menu.c32             :  not a COM32/COM32R module
 boot/syslinux/pci.c32              :  not a COM32/COM32R module
 boot/syslinux/pcitest.c32          :  not a COM32/COM32R module
 boot/syslinux/pmload.c32           :  not a COM32/COM32R module
 boot/syslinux/poweroff.c32         :  not a COM32/COM32R module
 boot/syslinux/prdhcp.c32           :  not a COM32/COM32R module
 boot/syslinux/pwd.c32              :  not a COM32/COM32R module
 boot/syslinux/pxechn.c32           :  not a COM32/COM32R module
 boot/syslinux/reboot.c32           :  not a COM32/COM32R module
 boot/syslinux/rosh.c32             :  not a COM32/COM32R module
 boot/syslinux/sanboot.c32          :  not a COM32/COM32R module
 boot/syslinux/sdi.c32              :  not a COM32/COM32R module
 boot/syslinux/sysdump.c32          :  not a COM32/COM32R module
 boot/syslinux/syslinux.c32         :  not a COM32/COM32R module
 boot/syslinux/vesa.c32             :  not a COM32/COM32R module
 boot/syslinux/vesainfo.c32         :  not a COM32/COM32R module
 boot/syslinux/vesamenu.c32         :  not a COM32/COM32R module
 boot/syslinux/vpdtest.c32          :  not a COM32/COM32R module
 boot/syslinux/whichsys.c32         :  not a COM32/COM32R module
 boot/syslinux/zzjson.c32           :  not a COM32/COM32R module


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[58984]) leaked on lvs invocation. Parent PID 4364: /bin/bash
```

---

### Post by oldfred on 2021-04-02
You posted you turned UEFI off and Legacy on.
Then if drive is still gpt, you have to have a bios_grub partition.
And then all the UEFI instructions can be ignored and you have to use old BIOS install instructions.
Do not mix BIOS & UEFI, use one or the other.

---

### Post by CatKiller on 2021-04-03
> **webmanoffesto said:**
> Okay, from boot menu I choose "UEFI - SanDisk Cruzer"
> **webmanoffesto said:**
> Single boot.
BIOS setup, System Configuration, is set to "Legacy Support Enable and Secure Boot Disable"
This combination is what you specifically need to avoid. If you do this, it won't boot.

Use UEFI **or** use Legacy. Don't mix and match, it won't work.

UEFI is preferable to Legacy.

---

### Post by ActionParsnip on 2021-04-03
If its a single boot, set to legacy and install. Much simpler.

---

### Post by webmanoffesto on 2021-04-03
The Ubuntu 20 install seems to progress successfully through many stages, then it stalls at "preparing to completely remove libreoffice-help-zh-cn (amd64)". What's the significance of that? Why stall there.

I choose minimal install and don't download updates, don't install third party items.

---

### Post by webmanoffesto on 2021-04-03
I now have a working installation of Ubuntu 20. I'm not sure exactly got it working, maybe the Ubuntu 20 LiveDisk on DVD which seemed to stall at "removing libre-office" was enough to install a working installation.

---

### Post by webmanoffesto on 2021-04-04
Now on boot I'm getting a nonstop scrolling "pcieport 0000:00:03.0: PCIe Bus Error"
What causes this?
I think I got this before and I think I fixed it with
[https://itsfoss.com/pcie-bus-error-severity-corrected](https://itsfoss.com/pcie-bus-error-severity-corrected)/
```

# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"
# 9/14/2020, 19:22
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="pcie_aspm=off"

```
I booted off an Ubuntu Live DVD. I managed to mount sda2, which is my root partition. I edited GRUB.

---

### Post by CatKiller on 2021-04-04
> **webmanoffesto said:**
> But now I can't get to the Grub because on boot it goes straight to this "pcieport" error. 

On a single boot system the Grub menu won't be shown by default. You can invoke it by pressing the appropriate key at boot time. I think it's spamming the Escape key on UEFI systems or holding the Shift key on BIOS systems, but it could well be the other way round. Once you've got the Grub menu up it's E to edit the line that you boot with. 

> I can boot Ubuntu from a Flash drive. And I can navigate to /dev where sda1 is, which is where my grub file should be. But how do I edit it?

Just editing a file wouldn't be enough in this case; you'd need to mount the filesystem, edit the file, and run update-grub on the target machine. You can set up a chroot from a live USB to do it, which is fiddly but not super hard.

---

### Post by webmanoffesto on 2021-04-04
> **CatKiller said:**
> Just editing a file wouldn't be enough in this case; you'd need to mount the filesystem, edit the file, and run update-grub on the target machine. You can set up a chroot from a live USB to do it, which is fiddly but not super hard.
Well I managed to mount the partition (sda2) but the instructions I found are quite involved. Do I need to do all this? [https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

I believe that what I have is sda1 efi boot partition, sda2 root, sda3 home.

```

Since you say your grub bootloader appears, but the menu is empty, I think you don't need to reinstall grub, but rather, as you ask, run update-grub. To achieve this, you can use a Live CD, mount the relevant partitions from your hard disk, chroot into the mounted directory, and run update-grub, which should work as if you were operating on the actual hard disk.

Boot with your Live CD, selecting "Try Ubuntu without installing".

Once it boots, open a terminal (ctrl-alt-t) and mount your Ubuntu partition on /mnt. I'm assuming the Ubuntu partition is /dev/sda5, but you should determine this yourself. Let me know if you need help to do this:

sudo mount /dev/sda5 /mnt

Then mount a few more directories that are needed:

sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc

Also, if you have a separate Ubuntu boot partition (pretty uncommon these days, but it may be the case):

sudo mount /dev/sdaX /mnt/boot

How can you tell if you have a boot partition?

Once you have your Ubuntu partition mounted, open /mnt/etc/fstab. If you see an entry for /boot, note which device it is pointing to (/dev/sda4 maybe?). This is the one you have to mount.

Once these are mounted, do chroot to start using the mounted directory as the root partition:

sudo chroot /mnt

You'll get a #/ prompt. First thing to do is confirm that you're using the correct /boot directory. Go to /boot/grub and look at the files there. There should be a bunch of .mod files and a grub.cfg file. If the directory is empty, don't continue, because it means this is NOT your actual boot directory. Look above to see how to determine if you need to mount an additional boot directory.

Once you've confirmed that /boot/ contains the correct files, meaning that it is the correct location, type:

sudo update-grub

This should rebuild your /boot/grub/grub.cfg file with the menu entries.

Then exit the chroot:

exit

At this point you may want to check that things were correctly updated. For this, cd /mnt/boot/grub and check that grub's files are there, there should be a bunch of .mod files and grub.cfg, the latter should have entries for your Ubuntu kernels. If you only see grub.cfg and no .mod files, it means that this is NOT the correct boot directory, look above for how to mount a separate boot partition.

Unmount the filesystems:

sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/boot #Only if you mounted it earlier
sudo umount /mnt/

And then reboot, hopefully your Grub menu will be restored.


```

---

### Post by webmanoffesto on 2021-04-04
When I tried "Secure Boot Enable and Legacy Support Disable" I got "Selected boot image did not authenticate."

---

### Post by ActionParsnip on 2021-04-04
If it's not dual boot, why use UEFI ?

---

### Post by CatKiller on 2021-04-04
> **webmanoffesto said:**
> Do I need to do all this?

Not if you can invoke the Grub menu, no. Then you'd just edit the boot line to see if your fix works, then make it permanent if it does.

Otherwise, you can make the change permanent without testing with the chroot environment. I think you do need the bind mounts to the pseudo-filesystems, too, so that the update-grub script knows where to find things to set them up properly. 

The process is quite straightforward: since your own install isn't booting, you use the infrastructure of the live USB, which can boot. Then you **ch**ange the **root** of the commands that you're running, so that they take effect as if they were running on your install. It's a very useful troubleshooting thing. 

I have no idea if the fix you've found will have any effect, and I don't know how hard you've tried to bring up the Grub menu as an alternative, but the chroot method is a way that you can change your boot options without being able to boot and without having access to the Grub menu.

---

### Post by webmanoffesto on 2021-04-04
> **ActionParsnip said:**
> If it's not dual boot, why use UEFI ?
I'm really confused about this whole UEFI thing. I got a good price on the laptop, but now I'm fed up with this whole UEFI thing. 
Following the advice in one of the comments above I enabled Secure Boot, and then all I could get was "Selected boot image did not authenticate." Then I disabled secure boot, but now I'm back to the endless scrolling "pcieport 0000:00:1c.5: AER: PCIE Bus Error"

---

### Post by CatKiller on 2021-04-04
> **webmanoffesto said:**
> Following the advice in one of the comments above I enabled Secure Boot, and then all I could get was "Selected boot image did not authenticate."
No one here told you to enable Secure Boot.

---

### Post by oldfred on 2021-04-04
Since you did not install in UEFI Secure Boot mode, do not turn that on.

This says it may be an UEFI setting.
[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id)

With UEFI, you press escape key, perhaps more than once as finding the correct time between UEFI screen & when grub normally appears can be tricky. You then should get grub menu.

---

### Post by CatKiller on 2021-04-04
> **webmanoffesto said:**
> I'm really confused about this whole UEFI thing.

UEFI is the replacement for BIOS. It's the firmware for your computer. It overcomes a lot of the limitations that BIOS had. Because BIOS is so ancient and limited, your UEFI can emulate BIOS. That's what the Compatibility Support Module does. Booting in Legacy mode enables the CSM.

---

### Post by webmanoffesto on 2021-04-04
Okay, I have it set to Disable Secure Boot
then I selected Legacy Boot when booting the Flash Drive which has the Ubuntu 20 image.
I chose minimal install, don't upload updates, don't install 3rd party items. The install seemed to go very well. All the stages went quickly.
I have sda1: efi, boot, sda2: root (ext4, reformat), sda3 home (ext4, don't reformat)
Now when I try to boot the laptop I do F9 Boot menu, I select the legacy boot option.
And I get a grub prompt:  "Gnu Grub version 2.04 Minimal Bash like line editing is supported ... grub>"
After that I get "Boot Device not found. Please install an operating system on your hard disk. Hard Disk - (3F0)"

So I tried running Boot Repair Disk. But it said "The current session is in BIOS-compatability mode. Please disable BIOS-compatability/CSM/Legacy mode in your UEFI firmware and use this software from a live CD or live usb that is compatible with uefi booting mode. for example use a live usb of boot repair disk 64 bit ... after making sure your BIOS is in EFI mode. This will enable this feature." What feature? Updating Boot Repair Disk?

And I was running it off a flash drive (live USB). That is weird.

And when I Enable Secure Boot then I only get "Selected boot image did not authenticate" and I'm stuck on that screen.

---

### Post by oldfred on 2021-04-04
Did we not say "Do not turn on UEFI Secure Boot". That is just a waste of your time.
You have to install in UEFI Secure boot mode, which you cannot do if legacy mode is on.

Please review post #5.
If you want Legacy you will need a bios_grub partition.
If you want UEFI you need an ESP. (your FAT32 with boot flag).

Grub will not properly install to a gpt partitioned drive in BIOS/legacy/CSM mode, unless you have the bios_grub partition.
And then if you reinstalled in BIOS boot mode and try to boot, you get a grub boot error. You either booted in BIOS mode to a grub that was not fully installed, or booted in UEFI mode and old grub in UEFI mode is then not correct.

You have to decide if you want UEFI or BIOS/CSM/Legacy. And then always boot installer in that mode and then make sure system is set to boot installed system in that mode.
And understand what are requirements for your chosen boot mode.

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Note many new systems, now are eliminating CSM. That will simplify installs as then only UEFI installs will work.

---

### Post by CatKiller on 2021-04-05
> **webmanoffesto said:**
> And when I Enable Secure Boot
You seem confused on this point. **Secure Boot is designed to make things *not* work.** That is its function. Specifically, it is to prevent the execution of any code that has not been signed by someone that is trusted by the UEFI.

If something is not working, enabling Secure Boot will not make it work. If something *is* working, enabling Secure Boot may make it no longer work.

---

### Post by webmanoffesto on 2021-04-05
Trying to be more precise, I think someone pointed out that it didn't make sense that I created a mismatch when I 1. disabled Secure Boot but then 2. at the boot menu I booted the flash drive UEFI. Also, I don't really know what I'm doing. I'm hacking on this laptop and hoping that I can get it working.

---

### Post by CatKiller on 2021-04-05
> **webmanoffesto said:**
> Trying to be more precise, I think someone pointed out that it didn't make sense that I created a mismatch when I 1. disabled Secure Boot but then 2. at the boot menu I booted the flash drive UEFI. Also, I don't really know what I'm doing. I'm hacking on this laptop and hoping that I can get it working.

No, you created a mismatch by enabling Legacy and then booting the installer in UEFI mode, which will install in UEFI mode. That combination will not boot after installation. Disabling Legacy and booting the installer in Legacy mode also will not boot after installation. 

> **CatKiller said:**
> Use UEFI **or** use Legacy. Don't mix and match, it won't work.

---

### Post by webmanoffesto on 2021-04-05
Using GParted I deleted all partitions. I booted a Flash drive with Ubuntu 20 on it. I selected "erase everything and reinstall". I now seem to have a working laptop. 
The installer created
/dev/sda1, fat32, /boot/efi, 512 MB
/dev/sda2, extended, 900GB
... /dev/sda5, ext4, 900GB

When restarting the laptop I first went to boot menu and selected legacy boot.

I wonder what will happen if I don't go to Boot Menu / Legacy Boot first. I'm a bit scared to try.

This whole UEFI vs old BIOS thing is horrible. It screws me up. It is not like I learn this because my job requires me to partition laptops all the time. I run into this once every few years when I partition / install Ubuntu for myself or a family member. When my systems work as they should there is no reason for me to know anything about legacy BIOS versus new-fangled UEFI.

---

### Post by CatKiller on 2021-04-05
> **webmanoffesto said:**
> When restarting the laptop I first went to boot menu and selected legacy boot.

Why on Earth would you do such a thing?

> **CatKiller said:**
> Use UEFI **or** use Legacy. Don't mix and match, it won't work.

---

### Post by tea for one on 2021-04-05
> **webmanoffesto said:**
> Using GParted I deleted all partitions. I booted a Flash drive with Ubuntu 20 on it. I selected "erase everything and reinstall". I now seem to have a working laptop. 
The installer created
/dev/sda1, fat32, /boot/efi, 512 MB
/dev/sda2, extended, 900GB
... /dev/sda5, ext4, 900GB

When restarting the laptop I first went to boot menu and selected legacy boot.

I wonder what will happen if I don't go to Boot Menu / Legacy Boot first. I'm a bit scared to try.

This whole UEFI vs old BIOS thing is horrible. It screws me up. It is not like I learn this because my job requires me to partition laptops all the time. I run into this once every few years when I partition / install Ubuntu for myself or a family member.

Two primary partitions and then sda5 together with an ESP identified as sda1.

I can't see how the installer would do this as a fresh installation?

This is a old-style MBR partition scheme with a new EFI partition - very unusual..............

Can you post the output in code tags ```
sudo parted -l
```

---

### Post by Dennis N on 2021-04-05
> Two primary partitions and then sda5 together with an ESP identified as sda1. I can't see how the installer would do this as a fresh installation?
Strange but true. Do a BIOS mode install, choose "Erase Disk and Install" and this is the result. Here's a confirming case from a VM install of Ubuntu 20.04:
```
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4
```

---

### Post by webmanoffesto on 2021-04-05
> **CatKiller said:**
> Why on Earth would you do such a thing?
Do you mean why would I boot using bios boot?
I had already turned off secure boot. And now when I selected bios boot. I think those two match. 
How that fits into how the Ubuntu installer and the fat32 /boot/efi partition, I don't know.

Would it be more correct to do UEFI boot or legacy BIOS boot now?

---

### Post by webmanoffesto on 2021-04-05
> **tea for one said:**
> Two primary partitions and then sda5 together with an ESP identified as sda1. I can't see how the installer would do this as a fresh installation? This is a old-style MBR partition scheme with a new EFI partition - very unusual. Can you post the output in code tags "sudo parted -l"

Here's the output
```
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

[FONT=courier new]Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   1000GB  1000GB  extended
 5      539MB   1000GB  1000GB  logical   ext4
[/FONT]
sudo fdisk -l
Disk /dev/loop0: 55.48 MiB, 58159104 bytes, 113592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdd28ceae

[FONT=courier new]Device     Boot   Start        End    Sectors  Size Id Type
/dev/sda1  *       2048    1050623    1048576  512M  b W95 FAT32
/dev/sda2       1052670 1953523711 1952471042  931G  5 Extended
/dev/sda5       1052672 1953523711 1952471040  931G 83 Linux
[/FONT]
Disk /dev/loop8: 138.84 MiB, 145563648 bytes, 284304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


```

---

### Post by tea for one on 2021-04-05
Both examples from Dennis N and webmanoffesto have certainly surprised me.

I assume that this is a result of using a msdos partition table?

It would indicate that the current Ubuntu installer creates unexpected results (other than the usual problem of ignoring the user choice of grub destination).

Moreover, it would be relevant to encourage the use of gpt (partition scheme) and UEFI mode installations to try and avoid this unusual result.

---

### Post by ajgreeny on 2021-04-05
At the risk of overcomplicating the situation which has totally baffled you I suspect you may do better to trash everything so far and start again completely clean. Make sure that the computer is setup to use UEFI, not legacy or CSM and also ensure **Secure boot is disabled** in the UEFI setup.
I suggest then using **gparted** on a **live OS booted in UEFI mode** to firstly create a new **GPT partition table** on the hard disk of the computer but not bother about creating any partitions.

Now boot to your **live install USB in UEFI mode** and let that carry out a default installation using the whole hard disk.  The installer will then create all the needed partitions for you and you will not have to bother about the details.

You will end up with a small (~200 - 500M) fat32 ESP/EFI partition, and a large ext4 partition for / (root) with everything else needed included in it.  **It is essential that you boot the live USB in UEFI mode to do this**.

---

### Post by webmanoffesto on 2021-04-05
> **ajgreeny said:**
> At the risk of overcomplicating the situation
I would be willing to try that. Do you think I could also use GParted to create the boot partition, the / root and the /home partitions?
How would I do that?

---

### Post by tea for one on 2021-04-05
Boot a live session in UEFI mode
Use gparted to **only** create a **gpt** partition table

Then let the installer automatically create the partitions.

[COLOR="#0000FF"]ajgreeny[/COLOR] already mentioned this.

---

### Post by oldfred on 2021-04-05
It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first. Use menu, device at top of gparted:
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

You can use gpt with either BIOS or UEFI.

I used gpt with BIOS starting in 2010 with another drive as MBR for Windows XP on my BIOS only system.
The only reason to use MBR, is if you have an old system and have to boot Windows in BIOS mode. Or a few users who just like BIOS boot.

There are 3 boot modes.
UEFI with Secure Boot on.
UEFI (Secure boot off)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You cannot boot in CSM mode with Secure boot on.
Some systems must be in UEFI only to boot in UEFI mode. Mine would not boot in UEFI mode with the UEFI or CSM setting.
Some also require a separate UEFI setting to allow USB boot, as that is not Secure. Required, if you have it, whether using Secure boot or not.

Some installers like Rufus create UEFI only or BIOS/CSM only installers. How you boot install media is then how it installs, so you have to first create installer in the mode you want. 
Other installers create create a flash drive that can be booted from UEFI boot menu, either UEFI:xxxx or xxxx, where you choose whether you are booting in UEFI mode or CSM mode.

---

### Post by ajgreeny on 2021-04-05
> **webmanoffesto said:**
> I would be willing to try that. Do you think I could also use GParted to create the boot partition, the / root and the /home partitions?
How would I do that?
I think that you are again making things more complicated for yourself and unless you really do have a need for a separate /home partition I would keep things as simple as possible until you are a bit more *au-fait* with the whole UEFI/CSM/BIOS and GPT/msdos story, which at present is where your knowledge seems to be very limited.

I am not sure if you've been pointed to the Ubuntu help page on UEFI at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), but if not read through it and make sure that you understand all the points that it makes if you do decide to attempt using separate partitions.

You mention a separate /boot partition but that is not something that you want or need; you will however need an EFI partition, the small ~200M fat32 partition I mentioned in my last post; all details of this are in the linked page mentioned above in the ***Creating an EFI System Partition*** section.

For the root and /home partitions, if you decide you really must have them, create them either with gparted before installing as ext4 partitions or during the installation.  You will need around 30G for / (root) and all the remaining disk space (excluding the EFI partition) as /home.
During installation click on the root partition space, then click on Change button (or is it Edit, I can't remember), choose to **Use as ext4**, make the mountpoint / and select format partition if it's not already selected.

For the larger /home partition you do more or less the same, **Use as ext4** but of course use /home as the mountpoint and as this is the first installation on this machine again select format.  In future when your /home partition has all you personal data files on it you will need to make sure that the format box is not selected or you will lose all data.

I hope this helps you; assuming you have installed previously using legacy BIOS with separate root and /home partitions, this is not really much different other than the need for that small fat32 EFI partition, but a default install using the whole disk will remove any possible problems that may otherwise occur simply because this is all new to you.  If necessary you can always start again and choose the default method if the manual partitioning becomes too onerous a task.

Whichever you choose, good luck!

---

### Post by webmanoffesto on 2021-04-07
The install was going well, then it stalled at "Running post-installation trigger linux-image-5.8.0-48-generic (amd64)
That said "post installation" which made me optimistic.
I rebooted (without touching the boot menu) and the laptop is now running Ubuntu.
I hope it keeps working.

The new partitioning makes a lot more sense.

fdisk
```

Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BAF30286-D548-4941-BBEA-20F79C161DBB

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem

```

---

### Post by ajgreeny on 2021-04-08
So it appears that you didn't bother with a separate /home partition but have simply a single partition for the OS and the necessary EFI partition.
That probably makes most sense at the current time; maybe when you come to your next installation you will know a lot more about UEFI, partitions and Linux in general giving you more confidence to try out the separate /home partition.

Anyway, good luck with the new installation!

---

### Post by webmanoffesto on 2021-04-08
> **ajgreeny said:**
> So it appears that you didn't bother with a separate /home partition but have simply a single partition for the OS and the necessary EFI partition ... maybe when you come to your next installation you will know a lot more about UEFI, partitions and Linux in general giving you more confidence to try out the separate /home partition. 

I like the idea of installing Ubuntu to root and putting files in Home. But this time, after so much trouble, I just created the GPT partition table, that left the entire disk "unallocated", and then I let the Ubuntu installer do it's thing. 

Thank you to everyone who helped me get this laptop working again.

---

### Post by ajgreeny on 2021-04-08
Great news! I'm glad we got there.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by webmanoffesto on 2021-04-11
Despite my "solved" label. I ran into the "pci error" problem again. It's either a non-stop scrolling pci error or a frozen screen full of "pci error". I had to do a clean install again.
Then I followed the instructions at
[https://itsfoss.com/pcie-bus-error-severity-corrected](https://itsfoss.com/pcie-bus-error-severity-corrected) and
[https://ahelpme.com/tag/pcie-bus-error/](https://ahelpme.com/tag/pcie-bus-error/)

Now my Grub says
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"
GRUB_CMDLINE_LINUX="pcie_aspm=off"

```

So far so good. I hope this laptop keeps working now.

---


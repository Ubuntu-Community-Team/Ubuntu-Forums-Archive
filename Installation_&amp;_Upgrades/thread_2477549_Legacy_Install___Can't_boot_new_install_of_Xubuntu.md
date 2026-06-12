---
title: "Legacy Install:   Can't boot new install of Xubuntu 22.04"
date: 2022-07-29
forum: Installation &amp; Upgrades
---

### Post by alforddm on 2022-07-29
This is a 10 yr old HP computer.   I used rufus with the BIOS and EFI option to get a bootable usb (creating a bootable usb from another Ubuntu install did not work).   There are no EFI options at all in the BIOS.   There is really not much to the BIOS, it's pretty basic.   Ubuntu 18.04 was previous installed on this system.   

It installs fine, then won't boot.   I used the wipe and install option.   Xubuntu is the only OS.   

Bios can't find hard drive.   I used the default install options the first time.   The second time, I used the BIOS boot options from this tutorial  [https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-22-04-lts.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-22-04-lts.html)  (still wouldn't boot)  and then tried boot-repair from the bootable usb with the default options.    

The third time, I created an EFI partition alongside all the options from the tutorial.     

I'm not sure what else to try.    Suggestions?   

The bootable USB runs fine.

---

### Post by oldfred on 2022-07-29
When you say BIOS cannot find drive, do you mean in Settings and list of drives? Or in a boot menu choice?

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by alforddm on 2022-07-29
I should have said, it doesn't find the OS.  It finds the hard drive it's self.   I'm going to do one more "wipe and install"  with the default options, just in case something messed up.   If it still won't boot, I'll post the boot-repair.   

Thanks for the quick response!

---

### Post by Impavidus on 2022-07-29
Sounds like an issue that affected many HP computers of around 2012: it looks at the description of the OS and only offers to boot if it's called Windows. An older thread on this subject: [https://ubuntuforums.org/showthread.php?t=2234019](https://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by oldfred on 2022-07-29
Many HP do not like any UEFI entry that does not say "Windows Boot Manager".

If only Ubuntu and installed in UEFI boot mode, we make the normal Ubuntu entry read as the Windows entry. It only checks description, not actual boot file. So you can have a Windows entry that boots grub/shim file.

When booting installer, you choose UEFI or BIOS with newer systems for booting USB flash drive.
And then your settings in systems UEFI must match default boot mode, or then either UEFI or BIOS.

Microsoft required vendors to install Windows 8 starting in 2012 in UEFI boot mode to gpt partitioned drives.
So if system is less than 10 years old, better to use UEFI with gpt.

Some very early UEFI systems had many bugs. Vendors had to update UEFI and Linux had to do many work arounds. Most now work ok, but some users still used BIOS boot with those early UEFI systems.

---

### Post by alforddm on 2022-07-29
I removed all the old partitions before the installation, just in case there was something odd hanging around,  then did a clean install of Xubuntu.    Still didn't boot.  The harddrive is found in the BIOS but the OS is not found on boot.   

Here is the paste pin.   

```

boot-repair-4ppa200                                              [20220729_2040]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdg and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04 LTS on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GT218 [GeForce 8400 GS Rev. 3] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 6.08(6.8) from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


c152ec201c37b6e97bbc2207e49d1271   sda2/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda2/BOOT/mmx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sda2/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda2/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda2/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda2/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: B4A6C5E4-3C44-47CD-B23A-9F6C87B0F434
        Start        End    Sectors  Size Type
sda1     2048       4095       2048    1M BIOS boot
sda2     4096    1054719    1050624  513M EFI System
sda3  1054720 1953523711 1952468992  931G Linux filesystem
Disk sdg: 57.84 GiB, 62109253632 bytes, 121307136 sectors
Disk identifier: 0x3c7f8c22
      Boot Start       End   Sectors  Size Id Type
sdg1  *     2048 121307135 121305088 57.8G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA ST31000524AS:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
3:540MB:1000GB:1000GB:ext4::;
sdg:62.1GB:scsi:512:512:msdos:SanDisk Ultra:;
1:1049kB:62.1GB:62.1GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1                                               c6e1789e-5e5a-44da-a9e2-54f95c15afe6             
&#9500;&#9472;sda2 vfat     BCE0-A067                            d8ae3063-283a-426b-88db-8e4533d404c4             EFI System Partition
&#9492;&#9472;sda3 ext4     71f03f5a-0e88-4e42-aebf-49635f26802f ae34bc4c-032c-4668-9658-789e997e3993             
sdc                                                                                                   
sdd                                                                                                   
sde                                                                                                   
sdf                                                                                                   
sdg                                                                                                   
&#9492;&#9472;sdg1 vfat     18F6-095B                            3c7f8c22-01                          XUBUNTU 22_ 

Mount points (filtered): _______________________________________________________

                        Avail Use% Mounted on
/dev/sda2              506.7M   1% /mnt/boot-sav/sda2
/dev/sda3              858.9G   1% /mnt/boot-sav/sda3
/dev/sdg1               55.3G   4% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda2              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3              ext4            rw,relatime
/dev/sdg1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 71f03f5a-0e88-4e42-aebf-49635f26802f root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   71f03f5a-0e88-4e42-aebf-49635f26802f
Ubuntu, with Linux 5.15.0-43-generic   71f03f5a-0e88-4e42-aebf-49635f26802f
Ubuntu, with Linux 5.15.0-25-generic   71f03f5a-0e88-4e42-aebf-49635f26802f
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=71f03f5a-0e88-4e42-aebf-49635f26802f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=BCE0-A067  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 656.698467255 = 705.124610048  boot/grub/grub.cfg                             1
 680.663005829 = 730.856337408  boot/grub/i386-pc/core.img                     1
   8.833568573 = 9.484972032    boot/vmlinuz                                   1
   5.474178314 = 5.877854208    boot/vmlinuz-5.15.0-25-generic                 1
   8.833568573 = 9.484972032    boot/vmlinuz-5.15.0-43-generic                 1
   5.474178314 = 5.877854208    boot/vmlinuz.old                               1
   9.630931854 = 10.341134336   boot/initrd.img                                1
   9.388771057 = 10.081116160   boot/initrd.img-5.15.0-25-generic              1
   9.630931854 = 10.341134336   boot/initrd.img-5.15.0-43-generic              1
   9.388771057 = 10.081116160   boot/initrd.img.old                            1

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Apr 15 21:50 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15 21:50 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15 21:50 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15 21:50 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15 21:50 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19 13:21 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15 21:50 40_custom
-rwxr-xr-x 1 root root   215 Apr 15 21:50 41_custom

=========================== sda3/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

====================== sdg1/boot/grub/grub.cfg (filtered) ======================

Try or Install Xubuntu
Xubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdg1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```   

And here are a few shots of the bios.   As near as I can tell, it's not an EFI system.   There are no EFI options in the BIOS.   

[IMG]https://i.imgur.com/l1vh9b0l.jpg[/IMG][IMG]https://i.imgur.com/uD11URXl.jpg[/IMG]

---

### Post by oldfred on 2022-07-29
You have both an ESP - efi system partition as sda2 for UEFI boot, and a bios_grub partition sda1, with grub in gpt's protective MBR.

The fstab shows UEFI install.
So you have to have system set to boot in UEFI boot mode, not BIOS/Legacy/CSM mode.

Even though to install you must have booted in UEFI boot mode, you rebooted in BIOS mode & ran Boot-Repair report. It misses some critical info.
At least run this after rebooting in UEFI mode.
sudo efibootmgr -v

Change boot mode to UEFI and then in UEFI boot menu do you have an "ubuntu" entry? It may not let you set that as default except by going into UEFI and changing boot order. When in UEFI mode, you should have UEFI options.
Some have had to update UEFI from HP to have all the updates you need.

---

### Post by tea for one on 2022-07-29
UEFI and/or Legacy may appear under Boot?

---

### Post by alforddm on 2022-07-29
There is no EFI option anywhere in the BIOS menu.   The only thing under the boot menu is boot priority.     I'll get a photo in a min.

> Even though to install you must have booted in UEFI boot mode   Pretty sure it booted in BIOS mode to install.   I had to use Rufus to with "EFI and BIOS" in order to get a bootable USB.    A regular boot disk created from another Ubuntu install would not boot.

Oh, and I'm not sure if it makes a difference or not, but originally this system came with Windows 7.

---

### Post by alforddm on 2022-07-29
Here is the boot menu.   Click on "hard drive" and it's just the hard drive listed again.  

[IMG]https://i.imgur.com/IhbvpD6l.jpg[/IMG]

---

### Post by oldfred on 2022-07-29
These lines only get added to fstab with an UEFI install:
> # /boot/efi was on /dev/sda2 during installation
UUID=BCE0-A067  /boot/efi       vfat    umask=0077      0       1

Microsoft required UEFI/gpt with release of Windows 8, but some systems that were Windows 8 were downgraded to Windows 7, so they still could have been UEFI.

---

### Post by Impavidus on 2022-07-30
I've got an HP laptop from 2011, so that's about the same age as yours. It says it supports UEFI, but I kept it in legacy mode. It was in legacy mode with a preinstalled Windows 7 when I got it. I didn't know the details back then, but it was probably best, as it avoided those complications with HPs not booting non-Windows systems. There's no Windows on it now, only two Xubuntu releases (the latest and an old LTS as a backup).

I've seen reports of recent Ubuntu releases automatically creating an empty EFI partition on install, even when you install in legacy mode. This EFI partition isn't empty, indicating that at some point there must have been some confusion over UEFI/legacy mode.

"A regular boot disk created from another Ubuntu install" can be created in several ways. The simplest of them, cloning the .iso to a usb drive, creates a live usb that works in both bios and uefi.

---

### Post by yancek on 2022-07-30
You must have done 2 or more installations as that is the only way you would have a BIOS Boot and an EFI partition, both of which show in the boot repair.  sda1 is the BIOS Boot and sda2 is the EFI partition.  Do you have Legacy/CSM enabled in the BIOS?  

A windows 7 that was installed on the computer when you bought it would have almost certainly been a Legacy install but could have been UEFI.
If you don't see any UEFI options in the BIOS, set it to Legacy/CSM.  It should boot as you have the BIOIS Boot partition as well as the core.img file installed.

---

### Post by alforddm on 2022-07-30
> **yancek said:**
> You must have done 2 or more installations as that is the only way you would have a BIOS Boot and an EFI partition, both of which show in the boot repair.  sda1 is the BIOS Boot and sda2 is the EFI partition.  Do you have Legacy/CSM enabled in the BIOS?  

A windows 7 that was installed on the computer when you bought it would have almost certainly been a Legacy install but could have been UEFI.
If you don't see any UEFI options in the BIOS, set it to Legacy/CSM.  It should boot as you have the BIOIS Boot partition as well as the core.img file installed.

I did do 3 installs.   However, before this last one, I deleted all the partitions, created one partition mounted at / and applied all the changes before I proceeded with the install.     I made these changes within in the installer, so they should be applied, right?   I can always redo it with gparted if you don't think the changes were made.   

I just looked through the thread about the HP computers only not wanting to boot if the EFI manager doesn't say WINDOWS.   I don't think this applies in this case.   I had this computer set up as a mythtv box with Mythbuntu 18.04 for several years without problems.   

So, if the system is an EFI system, but it's booting in BIOs mode, and there are no EFI options in BIOS, what do I do?   I tried looking for an updated BIOS yesterday, but didn't have any luck.  This system is no longer supported by HP and all the BIOS links I found were dead.

---

### Post by oldfred on 2022-07-30
From Boot-Repair booted in BIOS mode, reinstall grub.
That will install the BIOS boot version of grub or grub-pc.

---

### Post by alforddm on 2022-07-30
> **oldfred said:**
> From Boot-Repair booted in BIOS mode, reinstall grub.
That will install the BIOS boot version of grub or grub-pc.

I get this error when trying to reinstall grub.   

[IMG]https://i.imgur.com/JUIEDmkl.jpg[/IMG]

---

### Post by oldfred on 2022-07-30
At what point are you getting that screen?

Have you booted live installer in BIOS/Legacy/CSM mode? Not UEFI?
If in UEFI mode for live installer, it will want to repair/install grub in UEFI mode.

Advanced mode should let you choose install & choose drive to install grub into.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If not you can use chroot.
drs305 chroot to purge & reinstall grub2 - these are old BIOS instructions.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by alforddm on 2022-07-30
It was in the live installer and the error message says it's in BIOS compatibility mode.    Which is why it won't reinstall grub.  

When I went to advanced to reinstall grub, there is no /boot option only the /boot/efi

---

### Post by oldfred on 2022-07-30
It has been a long time since I have seen anyone use Boot-Repair to reinstall the BIOS version of grub. 
But I thought it still worked. Not sure if new issue or something in your BIOS/UEFI settings is confusing it.

You then need to chroot. Which was how we did it before Boot-Repair with BIOS.

---

### Post by tea for one on 2022-07-30
It has become quite difficult to provide precise help with boot-repair reports where the installation is in Legacy mode.

As an experiment, I've just installed Xubuntu 22.04 in Legacy mode and here are some details from a boot-repair report
3 partitions were created automatically:-
```
Disk sda: 59.63 GiB, 64023257088 bytes, 125045424 sectors
Disk identifier: 71AB9985-4F58-4CA4-8544-681F1370FA87
        Start       End   Sectors  Size Type
sda1     2048      4095      2048    1M BIOS boot
sda2     4096   1054719   1050624  513M EFI System
sda3  1054720 125044735 123990016 59.1G Linux filesystem
```
It will also show:-
```
# /boot/efi was on /dev/sda2 during installation
UUID=D289-BBF7  /boot/efi       vfat    umask=0077      0       1
```

@alforddm
After I installed Xubuntu 22.04 in Legacy mode (with 3 partitions as above), it did not boot first time.
Via the one time boot menu, I doubleclicked on the drive and it booted.

I also tried to repair Grub by using boot-repair in a live session.
After experimenting with a variety of Advanced Options (boot-repair), none worked and I turned to the terminal.
I could not get Grub to install or re-install to a working solution via the terminal (live session).

I think that the bios partition (sda1) and the EFI partition (sda2) somehow impede these repair attempts.

Now, the following is a method of [COLOR="#0000FF"]Legacy mode[/COLOR] installation, which booted as normal.

Boot into a live session of Xubuntu 22.04
Open Gparted
Create an [COLOR="#0000FF"]msdos[/COLOR] partition table
Create [COLOR="#0000FF"]one[/COLOR] partition Ext4 but _not_ using the complete disk (I used 50% of disk space)
Start the installer
Installation type - choose something else
Locate your prepared partition, use as ext4, format, mountpoint = root /
Grub bootloader to /dev/sda
Allow installer to continue

It worked for me and hopefully, it will work for you.

---

### Post by alforddm on 2022-08-01
@tea for one

Thank you so much for going to all that trouble!   It  worked.

---

### Post by tea for one on 2022-08-01
> **alforddm said:**
> @tea for one
Thank you so much for going to all that trouble!   It  worked.
Splendid - Happy to have helped.

It is beneficial to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

If the thread title could include the word Legacy, then it would be more relevant to people with a similar problem.

---


---
title: "Cannot boot into Ubuntu"
date: 2023-12-21
forum: Installation &amp; Upgrades
---

### Post by thevgamer on 2023-12-21
Hello Ubuntu forum ):P,

I installed Ubuntu 3 days ago, and when I boot into Ubuntu it didn't recognize Ubuntu, it gives me the error: "cannot find boot device". I have tried everything, for example: reinstall Ubuntu, and to add Ubuntu in the bios, but it wouldn't add that. So I was wondering if you could do it.

Here are my specs:
Intel® Core™2 Duo CPU T5750 @ 2.00GHz × 2
4 GB of memory
1 terabyte SSD

```
here is the pastebin:

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file
boot-repair-4ppa2068 [20231221_1408]

============================== Boot Info Summary ===============================

=> Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048
of the same hard drive for core.img. core.img is at this location and
looks for (,gpt3)/boot/grub. It also embeds following components:

modules
---------------------------------------------------------------------------
fshelp ext2 part_gpt biosdisk
---------------------------------------------------------------------------
=> Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of
the same hard drive for core.img. core.img is at this location and looks
for (hd0,msdos1)/boot/grub. It also embeds following components:

modules
---------------------------------------------------------------------------
biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
---------------------------------------------------------------------------

sda1: __________________________________________________________________________

File system: BIOS Boot partition
Boot sector type: Grub2's core.img
Boot sector info:

sda2: __________________________________________________________________________

File system: vfat
Boot sector type: FAT32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi
/efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi
/efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda3: __________________________________________________________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 22.04.3 LTS
Boot files: /boot/grub/grub.cfg /etc/fstab /etc/default/grub
/boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

File system: ntfs
Boot sector type: Windows 7/2008: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files: /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1: Ubuntu 22.04.3 LTS on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: G86M [GeForce 8400M GS] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.27 from Acer
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


a9c517741ac31962d7feb152948ad1ee sda2/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc sda2/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e sda2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc sda2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3 sda2/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3 sda2/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda : is-GPT, hasBIOSboot, has---ESP, not-usb, not-mmc, has-os, no-wind, 2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2 : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, not-far
sda3 : is-os, 64, apt-get, signed grub-pc grub-efi , grub2, grub-install, grubenv-ok, update-grub, end-after-100GB

Partitions info (2/3): _________________________________________________________

sda2 : is---ESP, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
sda3 : isnotESP, fstab-has-goodEFI, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot

Partitions info (3/3): _________________________________________________________

sda2 : not--sepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
sda3 : not--sepboot, with-boot, fstab-without-boot, not-sep-usr, with--usr, fstab-without-usr, std-grub.d, sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 38F6E2CA-F28B-4B57-B89D-AA91656C1DC3
Start End Sectors Size Type
sda1 2048 4095 2048 1M BIOS boot
sda2 4096 1054719 1050624 513M EFI System
sda3 1054720 976771071 975716352 465.3G Linux filesystem
Disk sdb: 57.3 GiB, 61530439680 bytes, 120176640 sectors
Disk identifier: 0x9632f465
Boot Start End Sectors Size Id Type
sdb1 * 2048 120176639 120174592 57.3G 7 HPFS/NTFS/exFAT

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:gpt:ATA Samsung SSD 870:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
3:540MB:500GB:500GB:ext4::;
sdb:61.5GB:scsi:512:512:msdos: USB SanDisk 3.2Gen1:;
1:1049kB:61.5GB:61.5GB:ntfs::boot;

blkid (filtered): ______________________________________________________________

NAME FSTYPE UUID PARTUUID LABEL PARTLABEL
sda
&#9500;&#9472;sda1 115c2b5c-d444-4ff8-bb03-61532842922f
&#9500;&#9472;sda2 vfat D10D-0C8C 18569ba1-65fe-4479-a876-909078f4369f EFI System Partition
&#9492;&#9472;sda3 ext4 9bd304ce-8896-4c79-974a-75fead424382 81bc60d7-ab90-4130-9410-9e9e6fcef740
sdb
&#9492;&#9472;sdb1 ntfs 9CC0A78BC0A769EA 9632f465-01 Ubuntu 22_04_3 LTS amd64

Mount points (filtered): _______________________________________________________

Avail Use% Mounted on
/dev/sda2 505.9M 1% /mnt/boot-sav/sda2
/dev/sda3 419.9G 3% /mnt/boot-sav/sda3
/dev/sdb1 52.5G 8% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda2 vfat rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3 ext4 rw,relatime
/dev/sdb1 fuseblk rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 9bd304ce-8896-4c79-974a-75fead424382 root hd0,gpt3
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu 9bd304ce-8896-4c79-974a-75fead424382
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda3 during installation
UUID=9bd304ce-8896-4c79-974a-75fead424382 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda2 during installation
UUID=D10D-0C8C /boot/efi vfat umask=0077 0 1
/swapfile none swap sw 0 0

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda3: Location of files loaded by Grub ====================

GiB - GB File Fragment(s)
243.175739288 = 261.107961856 boot/grub/grub.cfg 1
222.866970062 = 239.301586944 boot/grub/i386-pc/core.img 1
384.664215088 = 413.030055936 boot/vmlinuz 2
221.297000885 = 237.615845376 boot/vmlinuz-6.2.0-26-generic 1
384.664215088 = 413.030055936 boot/vmlinuz-6.2.0-39-generic 2
221.297000885 = 237.615845376 boot/vmlinuz.old 1
243.143550873 = 261.073399808 boot/initrd.img 4
196.785068512 = 211.296358400 boot/initrd.img-6.2.0-26-generic 1
243.143550873 = 261.073399808 boot/initrd.img-6.2.0-39-generic 4
196.785068512 = 211.296358400 boot/initrd.img.old 1

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18 2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18 2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18 2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18 2022 30_os-prober
-rwxr-xr-x 1 root root 1372 Dec 18 2022 30_uefi-firmware
-rwxr-xr-x 1 root root 700 May 17 2023 35_fwupd
-rwxr-xr-x 1 root root 214 Dec 18 2022 40_custom
-rwxr-xr-x 1 root root 215 Dec 18 2022 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb1: Location of files loaded by Grub ====================

GiB - GB File Fragment(s)
?? = ?? boot/grub/grub.cfg 1


Suggested repair: ______________________________________________________________
 Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```

---

### Post by yancek on 2023-12-21
You did one install of Ubuntu in Legacy mode which is why you have a BIOS_boot partition (sda1) and another install in EFI mode with the EFI partition (sda2) with the Ubuntu boot files needed for an EFI boot.  The boot repair output shows you were booting in Legacy mode.  Boot in EFI mode from your BIOS, the sda drive set to first boot in the boot priority.  If you booted the installer in EFI mode, it should have installed boot files to the EFI partition which it appears to have done and it should also have created an entry in the BIOS firmware.  If it did not do that, something else went wrong so you might try the suggestion in boot repair.  You do need to boot the boot repair in EFI mode which you did not.

---

### Post by thevgamer on 2023-12-21
Hey yancek,

I couldn't find the efi mode in my bios. I also looked up on the internet, but unfortunately no luck. But where can you find the efi mode?

---

### Post by MAFoElffen on 2023-12-21
The Boot Repair Disk booted as UEFI (on it's own), but the Installer LiveUSB installed as BIOS Legacy...

As this is a brand new install... Recreate the Installer LiveUSB in Rufus > GPT, UEFI "only". 

Boot the installer LiveUSB. Use "Try". Open a terminal:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
Ensure it says it booted as "UEFI Firmware mode"

Start the installer and reinstall.

That is going to be the easiest and fastest way to correct all of that with nothing left that may be confused.

---

### Post by oldfred on 2023-12-21
Core2 Duo I thought were BIOS only. Not sure how you booted to get the ESP - efi system paratition for UEFI boot?
Your fstab even shows the normal mount of the ESP which is only from an UEFI install.

Google says that model Acer has 2.4GHz *Intel* Core i5-2430M Dual-Core which is UEFI. 
I do not think Linux still has a nVidia driver for the 8400gs, but Intel video on that chip is better anyway.
[https://www.videocardbenchmark.net/compare/73vs26/GeForce-8400-GS-vs-Intel-HD-3000](https://www.videocardbenchmark.net/compare/73vs26/GeForce-8400-GS-vs-Intel-HD-3000)

Acer has required "trust" is UEFI settings to allow boot of Ubuntu.
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

You may need newer UEFI/BIOS.
Most let you download a file into a FAT32 partition which UEFI can read directly. If only an .exe that is a Windows file.
You may be able to extract the update from the .exe or use Freedos bootable flash drive to run the .exe file.

---

### Post by MAFoElffen on 2023-12-21
@oldfred --
NVidia G86M [GeForce 8400M GS] will work with driver package nvidia-340. It's legacy, but is still in the repo's.

---

### Post by thevgamer on 2023-12-22
Hey MAFoElffen,

I've installed the ubuntu installer in GPT, but now the usb won't boot anymore. The bios can detect the USB but it cannot open it anymore.

---

### Post by thevgamer on 2023-12-22
Hey Oldfred,

I've tried to set a supervision passwaord, and once I have done it, the menu secure boot and select a uefi file menu didn't pop up. Do I perhaps have to update my bios? My bios version is 1.27.

---

### Post by oldfred on 2023-12-22
Every system should have latest firmware whether Linux or Windows.
There have been various virus that need both UEFI & kernel updates. So current is best for security. 

Now older thread, but may apply to your system. Some had posted they had to downgrade UEFI firmware to get it to work. Then another update fixed issue & users posted that newest UEFI firmware worked.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

Issues often common across models by vendor. Older Acer threads. Newer version of Ubuntu should be better.
[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)

---

### Post by thevgamer on 2023-12-22
> **oldfred said:**
> Every system should have latest firmware whether Linux or Windows.
There have been various virus that need both UEFI & kernel updates. So current is best for security. 

Now older thread, but may apply to your system. Some had posted they had to downgrade UEFI firmware to get it to work. Then another update fixed issue & users posted that newest UEFI firmware worked.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

Issues often common across models by vendor. Older Acer threads. Newer version of Ubuntu should be better.
[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)

Ok I have read the showthreads, but I still can't see it. Here are some of my screenshots of my bios:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293232&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293233&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293234&stc=1[/IMG]

---

### Post by tea for one on 2023-12-22
> **thevgamer said:**
> I've installed the ubuntu installer in GPT, but now the usb won't boot anymore. The bios can detect the USB but it cannot open it anymore.
Disable Quick Boot (image no. 1 in post 10)

---

### Post by oldfred on 2023-12-22
In addition, I assume (?) that this issue has been fixed. But another reason to have latest firmware.
[https://www.phoronix.com/scan.php?page=news_item&px=Samsung-860-870-More-Quirks](https://www.phoronix.com/scan.php?page=news_item&px=Samsung-860-870-More-Quirks)

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows. Its a bootable ISO like a live installer that has to be extracted with tools, but only for firmware update.

If you can boot, you can see SSD revision & compare to what update is available.
udisksctl status

UEFI/BIOS firmware version:
sudo lshw | grep -m 1 -A 5 "*-firmware"

---

### Post by thevgamer on 2023-12-23
> **tea for one said:**
> Disable Quick Boot (image no. 1 in post 10)

Hey tea for one,

I've tried to boot with the quick boot disabled, but it still gives me the error message.

---

### Post by thevgamer on 2023-12-23
> **oldfred said:**
> In addition, I assume (?) that this issue has been fixed. But another reason to have latest firmware.
[https://www.phoronix.com/scan.php?page=news_item&px=Samsung-860-870-More-Quirks](https://www.phoronix.com/scan.php?page=news_item&px=Samsung-860-870-More-Quirks)

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows. Its a bootable ISO like a live installer that has to be extracted with tools, but only for firmware update.

If you can boot, you can see SSD revision & compare to what update is available.
udisksctl status

UEFI/BIOS firmware version:
sudo lshw | grep -m 1 -A 5 "*-firmware"

I've runned the ISO, but it says that the latest firmware version is already been installed. Do you have any more suggetions?

---

### Post by thevgamer on 2023-12-23
@oldfred I am having an idea, my laptop only boots with the partition scheme MBR. In Rufus there is in the hidden drive properties with a option: add fixes for old BIOSes (extra partition, align). Could this fix the install process or is this only to boot off from a USB?

---

### Post by jeremy31 on 2023-12-23
You are probably going to have to format the hard drive to use ms-dos(MBR) partitioning for the BIOS to recognize any install.  I had a Toshiba laptop that was that way

---

### Post by oldfred on 2023-12-23
I am surprised if a BIOS can see whether drive is MBR or gpt.
UEFI does read the FAT32 partition flagged as ESP. 
But BIOS just jumps to MBR to start boot process. Gpt has the protective MBR that is identical to BIOS MBR.

I used gpt with my 2006 laptop when I removed XP and made it Ubuntu only. That was an old BIOS only system.

---

### Post by thevgamer on 2023-12-23
> **jeremy31 said:**
> You are probably going to have to format the hard drive to use ms-dos(MBR) partitioning for the BIOS to recognize any install.  I had a Toshiba laptop that was that way

Hey Jeremy 31,

Yes it is now booting into the USB! But what did you do to let your laptop boot into Ubuntu?

---

### Post by thevgamer on 2023-12-23
> **oldfred said:**
> I am surprised if a BIOS can see whether drive is MBR or gpt.
UEFI does read the FAT32 partition flagged as ESP. 
But BIOS just jumps to MBR to start boot process. Gpt has the protective MBR that is identical to BIOS MBR.

I used gpt with my 2006 laptop when I removed XP and made it Ubuntu only. That was an old BIOS only system.

Hmmmm intresting. I wonder why my laptop has missing features. But did you do the install of Ubuntu on your laptop with the [COLOR=#4D5156][FONT=Roboto]partition table?[/FONT][/COLOR]

---

### Post by oldfred on 2023-12-23
That old Toshiba laptop only had 1.5GB of RAM.

I essentially retired it when 12.04 expired. Battery & coin battery were bad, so only worked with power plugged in and had to reset BIOS clock each time I booted.

But I tried installing 20.04 Ubuntu desktop and with limited RAM, it would not install. but server version did install & I was able to add a lightweight gui (flashback/fallback).

I then tried to install Kubuntu as I use that on my desktops and was surprised it installed & ran reasonable well but slow.

Then new laptop had to go back to Dell, just as I was leaving for trip & wanted a laptop. I had a external SSD with 22.04 Kubuntu in UEFI boot mode. I was able to add a BIOS boot stanza on internal HDD for external SSD drive to directly boot install which made old laptop very functional as long as I did not try to load more than one larger app at a time. With old HDD, I would see a second or two of swap loading if I clicked on another app. With SSD it only hesitated a bit.

---

### Post by thevgamer on 2023-12-24
Hey @oldfred,

Do you perhaps know what this is? I get this every time I boot into the live cd of Ubuntu.

(Sorry for the bad quality, I had to take it quick.)

---

### Post by MAFoElffen on 2023-12-24
I looked up the error... And it came up with something  am familiar with.

You have a machine with an old Intel Core2 Duo... Intel Core2 Duo is a 64bit CPU, but... I have an early computer that has that CPU, but had early UEFI that had 32bit UEFI.

That error first came up (in a search on it) when trying to boot an Intel Core Duo when it had a 32bit EFI... So would boot as BIOS Legacy, and as 32bit UEFI.

I have an assembler .efi program that I run and tells me if EFI is 32bit or 64bit... That I got the code that I adapted from from here: [https://stackoverflow.com/a/53899019](https://stackoverflow.com/a/53899019)

For booting Grub2 on 32Bit UEFI, I installed... Then had to convert the boot type via 'grub-efi-ia-32'...

---

### Post by thevgamer on 2023-12-25
> **MAFoElffen said:**
> I looked up the error... And it came up with something  am familiar with.

You have a machine with an old Intel Core2 Duo... Intel Core2 Duo is a 64bit CPU, but... I have an early computer that has that CPU, but had early UEFI that had 32bit UEFI.

That error first came up (in a search on it) when trying to boot an Intel Core Duo when it had a 32bit EFI... So would boot as BIOS Legacy, and as 32bit UEFI.

I have an assembler .efi program that I run and tells me if EFI is 32bit or 64bit... That I got the code that I adapted from from here: [https://stackoverflow.com/a/53899019](https://stackoverflow.com/a/53899019)

For booting Grub2 on 32Bit UEFI, I installed... Then had to convert the boot type via 'grub-efi-ia-32'...

Hey MAFoElffen,
 
Can I make the .efi program in the live CD of ubuntu or do I have to install a other program?

---

### Post by MAFoElffen on 2023-12-25
I have not seen where you have came out and said which laptop brand and model it is. You never even said if it is a laptop. (And this is post #24...)

From you boot-info report, it said "Acer". In your photo's, it's a laptop.

I'm guessing it is an Acer AS5920-6959... I don't even see in the manual for that where it says it is capable of anything besides Legacy BIOS boot...

For an Installer LiveUSB or LiveDVD, do this
```

sudo dmidecode -t 0

```
Post the results within CODE Tags.

If it is UEFI capable, and you can get into the UEFI shell prompt, then do
```

smbiosview -t 0

```

---

### Post by thevgamer on 2023-12-26
> **MAFoElffen said:**
> I have not seen where you have came out and said which laptop brand and model it is. You never even said if it is a laptop. (And this is post #24...)

From you boot-info report, it said "Acer". In your photo's, it's a laptop.

I'm guessing it is an Acer AS5920-6959... I don't even see in the manual for that where it says it is capable of anything besides Legacy BIOS boot...

For an Installer LiveUSB or LiveDVD, do this
```

sudo dmidecode -t 0

```
Post the results within CODE Tags.

If it is UEFI capable, and you can get into the UEFI shell prompt, then do
```

smbiosview -t 0

```

This is the acer aspire 7720 (not with the G). But i'm gonna try it later. I hope my laptop will eventually run ubuntu. Happy holidays :D

---

### Post by MAFoElffen on 2023-12-27
Thank you... That was very helpful.

Here is the User manual and the BIOS setup utility for your laptop: [https://www.manualslib.com/manual/232591/Acer-Aspire-7720.html?page=45](https://www.manualslib.com/manual/232591/Acer-Aspire-7720.html?page=45)

It has an IDE controller, but the HDD type is SATA. It was released in 2007... It originally came out with Windows Vista.

It is "Legacy Boot Only". It is not capable of UEFI nor SecureBoot. If you look at that user manual, there is no mention of EFI anywhere in it.

So yes... It can be MS-DOS partitioned with Legacy boot. [COLOR=#ff0000]It might[/COLOR] be able to do a GPT partition table on the target hard disk, IF you install it with an added "bios_boot" flagged partition (unformatted) for Grub2 (legacy) to install to. But if not, it can still do Legacy boot with the old MS-DOS partition tables.

---

### Post by thevgamer on 2023-12-27
> **MAFoElffen said:**
> Thank you... That was very helpful.

Here is the User manual and the BIOS setup utility for your laptop: [https://www.manualslib.com/manual/232591/Acer-Aspire-7720.html?page=45](https://www.manualslib.com/manual/232591/Acer-Aspire-7720.html?page=45)

It has an IDE controller, but the HDD type is SATA. It was released in 2007... It originally came out with Windows Vista.

It is "Legacy Boot Only". It is not capable of UEFI nor SecureBoot. If you look at that user manual, there is no mention of EFI anywhere in it.

So yes... It can be MS-DOS partitioned with Legacy boot. [COLOR=#ff0000]It might[/COLOR] be able to do a GPT partition table on the target hard disk, IF you install it with an added "bios_boot" flagged partition (unformatted) for Grub2 (legacy) to install to. But if not, it can still do Legacy boot with the old MS-DOS partition tables.

Than you for searching this out for me, but I think I am going for the MS-DOS partition tables. The only problem is I have never done a MS-DOS partition tabel. So my question to you is, how do I do a MS-DOS partition tabel?

---

### Post by MAFoElffen on 2023-12-27
Boot from the Installer LiveUSB > Use "Try" > Start Gparted... Chose the disk from the pull-down on the right. Select "Device" from the Menu at the top. Selectr "Create Partition Table".

In the pop-up dialog, select "MS-DOS" for the type. Select "OK". Close GParted. (You do not have to click apply for that to work.)

Start the installer from the desktop...

Good luck! Have fun.

---

### Post by thevgamer on 2023-12-28
> **MAFoElffen said:**
> Boot from the Installer LiveUSB > Use "Try" > Start Gparted... Chose the disk from the pull-down on the right. Select "Device" from the Menu at the top. Selectr "Create Partition Table".

In the pop-up dialog, select "MS-DOS" for the type. Select "OK". Close GParted. (You do not have to click apply for that to work.)

Start the installer from the desktop...

Good luck! Have fun.

I've tried to do the installation with GParted, but I still got the message: "cannot find boot device." So I booted to the live CD of ubuntu and it again installed the GPT partition with EFI. I don't what I did wrong, but here are the steps I took:
1. I pressed the button: "try Ubuntu."
2. Then I went into GParted and choose the MS-DOS partititon.
3. I finaly went into the setup and choose: "delete hard drive and install Ubuntu."

I think there is something wrong with the last step I took, but I am not sure.

---

### Post by thevgamer on 2023-12-28
Hey yall, my laptop is finally running Ubuntu!

Well it turns out that you first had to make a MS-DOS partition table, then you need to click on the button: "other" so you can make the partitions by yourself, then you needed to make **ONE** partition for the boot and the system. So I created a root partition. Eventually the BIOS will detect the OS.

Thank you all for helping!

---


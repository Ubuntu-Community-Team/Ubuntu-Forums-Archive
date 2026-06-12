---
title: "Install Ubuntu 16.10 on 2nd hard drive"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by hardliner2 on 2016-11-04
Motherboard - MSI Z97 PC MATE
Primary HD - Samsung SSD 120 GB
Second HD - Western Digital 640 GB

Windows is running on Primary. I want to install Ubuntu 16.10 on Second HD. I created a bootable USB drive with Rufus to put Ubuntu on. During installation, it warns me of UEFI.

Last time I installed ignoring this comment, I wasn't able to boot into Windows anymore.

How do I install Ubuntu on the second HD and still be able to have the option to Windows?

---

### Post by alexjpowell on 2016-11-04
After the install, run this command:
sudo update-grub && sudo grub-install /dev/[BOOT PARTITION eg. Sda6]

If this does not allow GRUB to boot into Windows, please run this command and paste the output in this thread:
cat /etc/default/grub

---

### Post by ajgreeny on 2016-11-04
It sounds as if you may have installed Ubuntu in MBR or legacy BIOS mode which is never going to work properly as your Windows is obviously installed in UEFI mode, and to be able to use both OSs they must both be installed in the same mode.

See Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and tell us how to help get you up and running.

---

### Post by hardliner2 on 2016-11-05
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by hardliner2 on 2016-11-05
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Please write on a paper the following URL:
[http://paste2.org/UXUtP27M](http://paste2.org/UXUtP27M)

---

### Post by alexjpowell on 2016-11-05
> **hardliner2 said:**
> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Please write on a paper the following URL:
[http://paste2.org/UXUtP27M](http://paste2.org/UXUtP27M)

There is no way for me to flag this as the answer, but its the correct one

---

### Post by hardliner2 on 2016-11-05
I do not understand your response. I've tried looking for an answer that is simple enough for me to understand and can not find one.

Am I better off deleting Ubuntu and doing bootrec /fixmbr through Windows installation disk like I did last time?

---

### Post by oldfred on 2016-11-05
Your Windows is installed on sda in BIOS boot mode with MBR(msdos) partitioning.
Your Ubuntu is installed on sdb in UEFI boot mode with gpt(GUID) partitioning. 

How you boot install media is then how it installs, UEFI or BIOS.
Since Windows is in BIOS/CSM/Legacy boot mode best to convert Ubuntu to BIOS boot, but keep ESP - efi system partition for future use.
Windows can only be converted to UEFI with total reinstall & repartitioning to gpt. It only boots in BIOS mode from MBR and UEFI mode from gpt.

You can add a 1 or 2MB unformatted partition anywhere on sdb using gparted from live installer.
Then use Boot-Repair booted in BIOS mode to reinstall grub in BIOS boot mode to MBR of sdb. You want to keep sda's MBR as Windows.

Grub only boots working Windows and Windows 8 or 10 will keep turning on fast start/hibernation with updates which then grub cannot boot. Those with one drive, if they forget to turn off the fast start again, then grub will not boot Windows and they temporarily have to reinstall Windows boot loader to MBR. You would just have to use UEFI/BIOS to choose Windows drive to boot one  time.

There are some advantages to UEFI and gpt, but unless Windows is brand new install, probably not worth effort to reinstall Windows.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by hardliner2 on 2016-11-05
Make this simpler for me to understand.

---

### Post by oldfred on 2016-11-05
Use gparted to add a 1MB unformatted partition on sdb.
Use Boot-Repair's advanced options to install grub-pc for BIOS boot. Be sure to install to Ubuntu drive sdb.

---

### Post by hardliner2 on 2016-11-05
Gparted will not allow me to add a partition. What now?

---

### Post by oldfred on 2016-11-06
Are you using live installer's gparted?
You have to have all partitions unmounted. And even live installer usually mounts swap to speed the install, so you have to swap off or unmount it before you can change partitions.

Post this:
sudo parted -l

---

### Post by hardliner2 on 2016-11-06
I have GParted 0.25.0 installed.

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   120GB  120GB  primary  ntfs


Model: ATA WDC WD6401AALS-0 (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   623GB  622GB   ext4
 3      623GB   640GB  17.1GB  linux-swap(v1)

---

### Post by C.S.Cameron on 2016-11-06
Unplug your Windows hard drive before installing Ubuntu to the second hard drive.
After installing Ubuntu
- Shut down
- Plug in Windows hard drive
- Start BIOS
- Set Ubuntu drive as first hard drive
- Continue boot
- Run "update-grub" in Terminal to add Windows to grub boot menu.

---

### Post by hardliner2 on 2016-11-06
uh.. Ubuntu is already installed and after all the work I've done, I have no interest in formatting that hard drive again and starting over.

2nd. I've already ran "update-grub" and it made no difference.

You'll see that alexjpowell's comment stated that.

---

### Post by oldfred on 2016-11-07
You do not need 17GB for swap.
Hibernation is not really recommended and if you have more than 4GB of RAM, you may never use swap. I use 2 or 3GB.

Shrink swap and add a 1 or 2 MB bios_grub partition. Otherwise grub in BIOS boot mode will not install correctly.

---

### Post by C.S.Cameron on 2016-11-07
I like a large swap on my home entertainment thumb drive so that I can hibernate in the middle of a movie and come back to the same place the next evening. 
My understanding is that swap should be at least the size of RAM but nowadays that might be overkill.

I find gparted live works a lot better than what comes with Ubuntu.

---


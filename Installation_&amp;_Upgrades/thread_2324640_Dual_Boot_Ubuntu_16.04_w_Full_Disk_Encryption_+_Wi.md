---
title: "Dual Boot Ubuntu 16.04 w/ Full Disk Encryption + Win10 not encrypted (separate HDDs)"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by Abdul_Hakim on 2016-05-15
[FONT=verdana]Hello everyone,
[/FONT]
[FONT=verdana]I have 4 HDDs:[/FONT]

[LIST]
[*]60GB SSD
[*]500GB HDD - Win10 installed
[*]1 TB HDD (x2)
[/LIST]
[FONT=verdana]As you can see, the 500GB HDD has Win10 installed on it. The other drives are all currently empty.
[/FONT]
[FONT=verdana]I want to install Ubuntu 16.04 LTS (or 14.04, if 16.04 just won't work), with Full Disk Encryption, like so:[/FONT]

[LIST]
[*]60GB SSD - /
[*]1 TB HDD - /home
[*]1 TB HDD - extra storage, will mount it somewhere after installation
[/LIST]
[FONT=verdana]When the computer boots, I want GRUB to load and give me the choice of booting the Encrypted Ubuntu installation, or the non-encrypted Windows installation.[/FONT]
[FONT=verdana]During the Ubuntu installation, how do I partition my disks to make this happen? I've made several attempts and I just can't seem to figure it out.[/FONT]

---

### Post by oldfred on 2016-05-15
I do not know LVM nor encryption, but you need LVM which can span multiple drives.
The default install with UEFI uses both an ESP - efi system partition and a separate /boot partition that is outside the LVM.
Is Windows UEFI or BIOS? If system is newer it may be UEFI hardware but you still can install in UEFI or CSM mode. But can only dual boot from grub if Ubuntu is in same boot mode as Windows, both UEFI or both BIOS/CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

If UEFI, grub only installs to the ESP on the drive seen as sda. So you must have an ESP on sda.
Even if Windows is installed in BIOS boot mode which has to use MBR partitioning, you can use gpt partitioning on the Linux only drives. Windows will mount & read a NTFS partition on a gpt drive even when installed in BIOS mode.
But you must have Windows 10's fast start up off, as it will mount a shared NTFS partition which prevents Linux NTFS driver from mounting it.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html
[/URL]
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
Manually create
[URL="http://community.linuxmint.com/tutorial/view/2061"]http://community.linuxmint.com/tutorial/view/2061

[/URL]2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows) 

      Full disk encryption for two disk (ssd and hdd) setup ? 
[http://ubuntuforums.org/showthread.php?t=2312651](http://ubuntuforums.org/showthread.php?t=2312651)
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i) 
    [URL="http://community.linuxmint.com/tutorial/view/2061"]
[/URL] 

    [URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---

### Post by Abdul_Hakim on 2016-05-15
Oldfred you're everywhere lol you replied on my AskUbuntu thread too. 

Yeah I made sure to install Windows in UEFI mode, at least I'm pretty sure. When booting from the CD I made sure to select the UEFI option from the boot menu. Is there a way I can double check, just to make sure? I also didn't know about Win10's fast startup so I'll check on that as well. 

So just to clarify, on sda (/ for Ubuntu) I need both a /boot and ESP that are outside the LVM volumes for encryption? I'm mobile right now so I'll check out those resources you posted when I get home. Thanks for the help!

---

### Post by oldfred on 2016-05-15
I am retired and Ubuntu is my hobby. :)

I do not pay close attention, but if I notice same question in askubuntu, I do not usually answer there. 
I find this forum easier to use for back & forth issues.
AskUbuntu seems to be where you post one good solution and refer all others to that one solution, but less individual help. 

Still do not know LVM nor encryption, but have seen several Boot-Repair summary reports. And since both ESP and /boot are outside LVM with standard installs, then the reinstall/repair of grub is like a standard install, except you have to have LVM (and encrypt) drivers and mount the LVM as / (root) is inside it.

So yes normally ESP - efi system partition of 300MB plus or minus and /boot are outside LVM. 

Default install made /boot a little small. And UEFI installs often downloaded both standard & signed kernels so not a lot of room or /boot filled more quickly. And users were not housecleaning old kernels. 
With 16.04 it now only keeps two kernels by default.

---

### Post by Abdul_Hakim on 2016-05-15
Quick question, although I'm looking through your UEFI thread to see if I can find it. I'm using Rufus on Windows to create a bootable USB stick. Under Partition scheme and target system type, I have three choices:


[LIST]
[*]MBR Partition Scheme for BIOS or UEFI
[*]MBR Partition Scheme for UEFI
[*]GPT Partition Scheme for UEFI
[/LIST]

Which one is best?

EDIT:

I think this answers my question:

> [B]Two Drive installs - See also examples below

Both drives must be gpt partitioned. Best to include ESP - efi system partition as first partition on every gpt drive, even if booting from Windows efi partition. And grub only installs to ESP on sda.
Once you are booting with UEFI, best to have all drives and larger external devices even larger flash as gpt partitioned with an efi partition first even if just for future use. May have to manually edit UUID of efi partition, but Boot-Repair updated for two drive installs.

[B]Partitioning
With UEFI, gpt partitioning is (almost) required. If multiple drives all bootable drives need to be gpt and best if data drives are also gpt in case later you want to make it bootable. With gpt there is no primary, extended, logical partitions as in MBR(msdos) nor the 4 primary partition limit.
You can only have one efi partition per drive and with gparted you use the boot flag to assign it as the efi partition. No other partitions can have boot flag. Only if booting in BIOS mode with Ubuntu on gpt partitioned drive, you need a bios_grub partition.
Windows will only boot in UEFI mode so you cannot install Windows to gpt drive unless booting with UEFI.
I suggest 300MB efi partition - FAT32, 25GB /(root) - ext4, and then either /home - ext4, or /mnt/data partition(s). But you cannot do data partitions as part of install. 
If dual booting with Windows a shared NTFS data partition is also recommended.[/B][/B]

---

### Post by oldfred on 2016-05-15
The USB installer usually works with either MBR or gpt.
But a few computer's UEFI seem to require one or the other.

I have only used gpt for everything since about 2011, except one or two small flash drives that were just installers. But I have full installs or many ISO on one flash drive for mulitple boot/repair/install.

For UEFI boot only:
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition. I used gpt with my test of this.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by Abdul_Hakim on 2016-05-15
Okay so here's what I just tried:


[LIST=1]
[*]Removed the 500GB Windows drive from the system, so that only the three empty drives are connected

- /dev/sda 60 GB SSD, /
- /dev/sdb 1 TB HDD. extra storage, mounted after installation
- /dev/sdc 1 TB HDD, /home 
[*]Booted Ubuntu 16.04 from the USB Drive that was created with GPT partitioning 
[*]Previously I had ran gdisk from terminal to ensure that all three of these remaining hard drives had GPT partitioning. Although they're all empty, I made sure that they all had GPT partitioning tables (confirmed in Gparted) (also confirmed that the Windows drive is GPT earlier) 
[*]Ran Ubuntu installer 
[*]Created 300MB EFI partition on sda 
[*]Created 17GB Logical "Physical volume for encryption" partition on sda for swap 
[*]Created ~40GB Logical "Physical volume for encryption" partition on sda for / 
[*]Created 1 TB Logical "Physical volume for encryption" partition on sdc for /home 
[*]Created 1 TB Logical "Physical volume for encryption" partition on sdb for extra storage 
[*]Assigned mount points after creating the volumes for encryption 
(example: [http://linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/](http://linuxbsdos.com/2014/01/16/manual-full-disk-encryption-setup-guide-for-ubuntu-13-10-linux-mint-16/)) 
[*]Clicked Install Now, and I got this message: 

[http://imgur.com/Gg8N9Bj](http://imgur.com/Gg8N9Bj) 
[/LIST]

So since it's telling me I also need a /boot partition, based on what you've said, it seems that I need to create this /boot partition on sda outside of the encryption volumes, just like efi is, right?

I quit the installer (because for some reason, once you've created these partitions, the installer doesn't let you delete them), and went to Gparted to format all the drives and start again. On attempted to format sda, I get this error (which I've also ran into before):

[http://imgur.com/SDjIVSR](http://imgur.com/SDjIVSR)

So I guess I have to reboot and do it all again?

---

### Post by oldfred on 2016-05-15
All the default installs where they posted Boot-Repairs summary report had both an ESP and a /boot.

While an efi partion is used for UEFI boot, it is more equivalent to the MBR (sector 0) in BIOS/MBR. It only has boot code. In BIOS the MBR is so tiny more boot code is else where on system.
With UEFI most the start up boot code or grub is in ESP - efi system partition. But kernel and rest of grub is in /boot. 

The ESP is not a Linux /boot partition. 
The ESP must be FAT32 and the /boot must be a Linux format often ext2 since small or ext4 and probably journal not required.

There are some special configurations where you can use UEFI to directly boot kernel in ESP, but I have not seen that done, only mention somewhere that it is possible.

---


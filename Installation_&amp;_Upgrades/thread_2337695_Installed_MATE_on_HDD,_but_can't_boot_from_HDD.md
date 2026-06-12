---
title: "Installed MATE on HDD, but can't boot from HDD"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by normalcrayon on 2016-09-20
First, I made a USB boot drive, then I changed my boot order and booted from it under TRY MATE. Then I connected to the internet and activated the 16.04 Ubuntu MATE installer on the Desktop. I did a totally default installation, nothing out of the ordinary. To be clear, I selected erase drive and install Ubuntu MATE, so my HDD was formatted in the process.

The installation completed without any errors. Then I restarted my computer as was suggested to me in order to be able to save preferences and install programs. I installed a program, set up preferences, and then decided to make sure that my HDD was really a bootable device.

I shut down the computer, took out the USB, and turned on the computer. I changed my boot priority to put the HDD at 1st but when I left BIOS I was sent to a screen that told me to select a proper boot device and reboot or insert boot media in selected boot device and press a key. In other words, it failed to boot.

Finally, I booted again from the USB stick - I was given the same options as before, TRY or INSTALL ubuntu MATE (or OEM install/disc check) and I picked TRY. In the desktop, I checked the hard drive and I saw all the Ubuntu MATE installation folders, as well as the program that I installed earlier - on my HDD.

What's going on here? The smooth default installer installed onto my HDD but I can't boot from it. Do I need to specify a boot file path in BIOS for the HDD?

endnotes: I am using 16.04 LTS with 64 bit architecture on an ASUS computer. I torrented the iso file from the MATE official website and the USB stick I used is brand new and is 3.0 compatible (and I used it in a 3.0 slot)

---

### Post by normalcrayon on 2016-09-20
UPDATE: I did a TRY boot from the USB again, here is what the Disk app says about my drives:

500 GB Hard Disk
Referred to as the /dev/sda device (partition 1 is dev/sda1 etc)
Partitioning: GUID Partition Table
- It is partitiioned into 3 partitions and has 1.1mb of free space
Partition 1 (537 mb FAT 32bit - Not Mounted): Partition Type = EFI System
Partition 2 (495 GB Ext4 v1.0 - Not Mounted ): Partition Type = Linux Filesystem
Partition 3 (4.2 GB Swap v1 - Active): Partition Type = Linux Swap

32 GB Drive (USB)
Partitioning: Master Boot Record
Referred to as device /dev/sdb , has 47mb of free space
Partition 1 (32 GB FAT 32bit - Mounted at /cdrom): Partition Type = W95 FAT32 (LBA) (Bootable)

---

### Post by oldfred on 2016-09-20
You have installed in UEFI boot mode. Is UEFI Secure boot on or off. You can install either way, but then may need to change settings to boot actual install in same mode.

Some (now many) brands modify UEFI to also use description as part of boot. That is specifically not allowed per UEFI standard, but perhaps some large vendor of operating systems is suggesting that only "Windows Boot Manager" be allowed.

But there is a hard drive boot entry or fallback that still works. That is the same as booting flash drive. In UEFI the efi partition must have /EFI/Boot/bootx64.efi. Boot-Repair now will create/ or copy shimx64.efi to be that file if you tick/check option.

 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178) 

But your system may or may not have an UEFI entry to use that on hard drive. Post link to summary report from Boot-Repair.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Also if only booting Ubuntu, not Windows, you can change/add an entry to boot "Windows Boot Manager" that uses grub's shim. Details in link below in my signature.
       Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840) 
            Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)

---

### Post by normalcrayon on 2016-09-20
Thanks so much for your help.

Did what you said, but the pastebin ID that the pop up told me to write down (Hfnc0jzH) doesn't seem to exist. 

Also the HDD still doesn't seem to boot. 

I checked the Hard Drive by rebooting TRY Ubuntu Mate from the USB again and found boot/efi/ to still be empty

For what it's worth every time I load the USB I check for disk errors before loading Ubuntu and it always finds errors in 2 files.

---

### Post by oldfred on 2016-09-20
If errors in USB installer, it will not install correctly. 
Or is it an error on booting.
Need to know details on errors.

The /EFI/Boot on the installer is not the one we are worried about, but the one in your install, which to view you have to mount from installer and it will be in longer path. Often I do not see ESP on other drive in Nautilus and have to use Disks to mount the ESP on another drive.

---

### Post by normalcrayon on 2016-09-20
> **oldfred said:**
> If errors in USB installer, it will not install correctly. 
Or is it an error on booting.
Need to know details on errors.

The /EFI/Boot on the installer is not the one we are worried about, but  the one in your install, which to view you have to mount from installer  and it will be in longer path. Often I do not see ESP on other drive in  Nautilus and have to use Disks to mount the ESP on another  drive.
[http://paste2.org/ns6MIvKh](http://paste2.org/ns6MIvKh) Did another run through and got a working pastebin!

Sorry  I don't fully understand - the efi/boot contains two EFI files  (including bootx64.efi) on my USB stick,but on my harddrive the filepath  is boot/efi/ and it is empty.

The HD boot paths are all the  same, I just made a different one after installing MATE the first time  on it and after running this program. Mate newusb is the boot path I  have been using for all of this.

---

### Post by normalcrayon on 2016-09-20
Wait, I just realized, somehow the boot-repair changed my boot priority so that boot order 0000  (this new ubuntu named HDD path) ispriority 1. 

Now when I boot I get a GRUB boot menu with Ubuntu listed as an option! But it didn't seem to work. I chose Ubuntu and it just froze.

edit: Options are Ubuntu, Advanced Options for Ubuntu, EFI/ubuntu/fwupx64.efi, EFI/ubuntu/MokManager/efi.

Should I mess with booting from the two EFI file options?

---

### Post by normalcrayon on 2016-09-20
Good news! I ran a manual file system check on the etf partition and afterwards I was able to boot from the HDD right into the user account I made when I originally installed iton here.

If anyone sees this thread and wants to know what I did feel free to send me a message on here or on the normalcrayon account on the ubuntu mate forums. 

Thanks a ton to fred, you were a lot of help. Have a good night (or day!).

---

### Post by oldfred on 2016-09-20
Glad it is working.

You probably have two UEFI entries for Ubuntu. One is grub and one is shim (for secure boot). Shim works for standard UEFI without secure boot, so not sure why they still have grub?

You can remove entries and also removed the Windows folder in the ESP and the Windows entries in UEFI. But backup entire ESP first just in case.
From your install, the ESP is mounted read only. So to remove files you have to either change mount permissions in fstab and reboot, or use live installer. Then you can remove the /EFI/Microsoft folder.

       sudo efibootmgr -v 

 The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
Examples:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---


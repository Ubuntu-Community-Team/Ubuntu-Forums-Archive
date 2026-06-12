---
title: "Dual boot help"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by pat000 on 2015-10-29
I have Ubuntu installed on a separate disk drive than my Windows installation. I use the BIOS setting to select which disk to boot. I like to keep Windows and Ubuntu completely separate. This worked great until I recently upgraded to Ubuntu 14.04LTS. I forgot to unplug the Windows disk before the upgrade, and it appears that the Ubuntu upgrade installed grub on the Windows disk drive. Fortunately, I am still able to boot both Windows and Ubuntu through the grub menu, but I can no longer boot each drive separately. I get the grub rescue prompt if I tried to boot either drive by itself (by unplugging the other). I like to restore my original configuration. I downloaded and executed the bootinfoscript. Would someone please decipher how it is actually booting and suggest a best course of action? I am puzzled on which disk is it actually booting from. I have attached the output of the script. Thanks.

---

### Post by oldfred on 2015-10-29
You can quickly install grub to sdb, and using your Windows repairCD or flash drive run the fixMBR comand to restore a Windows boot loader to sda. Best to have Windows repair disk, but if just a Windows type boot loader desired you can use Boot-Repair to do that.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

But grub remembers where to reinstall on a major update. Best to reset that to sdb also:
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on major updates 
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by pat000 on 2015-10-30
Thanks for the detailed instructions. I have some follow up questions before proceeding. From the output of the deb-conf command, it appears that I am booting from the grub installed in sda. 

- The grub config in sda must have an entry to both Windows in sda and Ubuntu in sdb? How do I check?

- If I reinstall grub to sdb (location of my Ubuntu), will I still be able to boot windows through the grub (before fixing the Windows boot with the recovery disc)?

$ sudo debconf-show grub-pc
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/hidden_timeout: true
  grub2/kfreebsd_cmdline:
  grub-pc/partition_description:
  grub2/device_map_regenerated:
  grub-pc/postrm_purge_boot_grub: false
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD10EADS-00M2B0_WD-WCAV51704202 <== this is the drive with my Windows install
* grub2/linux_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/install_devices_empty: false
* grub2/linux_cmdline_default: quiet splash
  grub-pc/timeout: 10
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_failed: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/disk_description:
  grub2/kfreebsd_cmdline_default: quiet splash


$ sudo parted -l
Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  977GB   977GB   primary  ntfs         boot
 2      977GB   1000GB  22.7GB  primary  ntfs


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  577GB   577GB   primary   ext4            boot
 2      577GB   1000GB  423GB   extended                  lba
 5      577GB   913GB   336GB   logical   ntfs
 6      997GB   1000GB  3219MB  logical   linux-swap(v1)

---

### Post by oldfred on 2015-10-30
You set BIOS to boot sdb and grub will include an entry to boot Windows, if Windows is working.
Grub does not boot Windows that is hibernated or needs chkdsk or has major issues.
Then when you get Winodws issues, you may be able to directly boot Windows from sda via BIOS or one time boot key, or have to use your Windows repair disk to fix it.

If you run the dpkg to install grub to sdb, then you should check that grub-pc/install_devices shows the sdb drive. I think the quick install of grub to sdb (udo grub-install /dev/sdb) does not change default on major update reinstalls.

---

### Post by pat000 on 2015-10-30
Look like I screwed it up. I invoke this command to see where grub2 remembers to install before reinstalling grub per your instructions.

sudo dpkg-reconfigure grub-pc

I didn't see a way to cancel it, so left it at sda and let it finish.

Now I my worst fear has come true. I am not able to boot either. When I tried to boot from sda I get the following error:

"/boot/grub/i386-pc/normal.mod' not found and returned a grub rescue prompt. Should I reinstall grub with the live cd?

---

### Post by oldfred on 2015-10-30
Yes, but I would think you reinstall grub to sda. Does booting sda not work, or if you had grub already installed to sdb with the simple command that should also work.

You have to use keyboard to move & select/unselect choices
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions.

---

### Post by pat000 on 2015-10-30
I was able to achieve my goal with the boot-repair tool. I ran the tool the 1st time with the default configuration and it reinstalled grub on both drives. This allowed me to get back in both OSes. Next, pushing my luck, I unplugged the Linux drive and ran the tool again. This time it automatically figured out the Windows only installation and restored the MBR. I could not get a Windows repair disc since it is an OEM image. That is a great tool. Thanks again for your help.

---

### Post by oldfred on 2015-10-30
You do not have to unplug drive.
Boot-Repairs advanced mode lets you choose an operating system and drive to install boot loader into. That should have let you choose Windows & sda.

You should make your own repairCD or flash drive.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---


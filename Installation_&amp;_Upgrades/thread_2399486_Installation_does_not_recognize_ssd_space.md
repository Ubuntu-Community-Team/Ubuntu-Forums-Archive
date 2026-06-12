---
title: "Installation does not recognize ssd space"
date: 2018-08-25
forum: Installation &amp; Upgrades
---

### Post by srkasdorf on 2018-08-25
I am trying to install ubuntu in a dual boot and I'm running into a problem.  It says that 8.6gb is required for installation and only 8gb is available.  I created a live usb using rufus, departitioned 200gb on my ssd drive and left it unallocated.  I turned of secure boot settings in the bios.  I then used the shutdown command in the console to fully shut down windows.  Then I select to run from the usb in the boot menu.  It still does not recognize the space I left for it.  Does anyone have any input on this?

---

### Post by oldfred on 2018-08-25
Full shutdown with Windows is still not enough. You have to have fast start up or hibernation off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by srkasdorf on 2018-08-26
I did turn fast start off under power options>system settings.  Unfortunately it seems like it still wont work.  I agree that this is the problem but I cant figure out how to get windows to fully shutdown for some reason.

---

### Post by oldfred on 2018-08-26
Post these:
sudo parted -l
sudo gdisk -l /dev/sda

Sometimes there are other drive issues mostly caused by Windows.
It can convert to LDM/dynamic partitions, incorrectly convert drive from gpt to MBR if you install in 35 year old BIOS/MBR configuration and others.

---

### Post by srkasdorf on 2018-08-27
Unfortunately I can't run those commands because they are unix and not supported by windows.  I tried downloading the linux bash package on windows but it's in beta and it's not supported by the kernel.  Any other advice?  I'm thinking I might be creating the usb loader wrong.  I have been using rufus and creating the partition scheme as MBR and target system as BIOS or UEFI.  I looked at my partition properties and it says it is GPT, so I tried creating the usb with that as the partition scheme and target system as UEFI.  My system is EFI I believe.  When I try to create the usb that way, I select the usb in the boot menu but then it just boots up windows like normal. My main computer experience is coding for data analysis so I don't have much experience with this sort of thing.

---

### Post by oldfred on 2018-08-27
I thought issue was installing, not creating live installer.
Live installer should only need about 2GB.

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

Then you can boot live installer and run commands.

---

### Post by srkasdorf on 2018-08-27
Yes it is an installation issue, but because it won't recognize my ssd correctly I figured maybe one cause could be that I was creating the usb incorrectly.  I ran the commands in linux and recieved this result:

ubuntu@ubuntu:~$ sudo parted -l
Model: Verbatim STORE N GO (scsi)
Disk /dev/sda: 7969MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7969MB  7968MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 15564800 sectors, 7.4 GiB
Model: STORE N GO      
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 509A14E5-8B39-4997-BBE3-048F9CC9F78F
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 15564766
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        15564799   7.4 GiB     0700  Microsoft basic data

I am noticing that even with fast startup disabled, when I shut down the computer and start windows again it is remembering webpages which means it's not shutting down fully like it should.  I don't know how else to get it to fully shut down which is why I tried the shutdown command in terminal.

---

### Post by oldfred on 2018-08-27
That only showed USB flash drive.

Are you sure you have Windows fast start up off? Review the instructions posted above. 
Even if you just turn it off, but reboot Windows may do an Update and turn fast start up back on. 
I changed my one Windows system to have more control over updates, but it changed that also and I find it rebooted system and is running updates.

Many systems also need UEFI update from vendor.
And if a newer NVMe SSD or many Samsung SSD, you may also need firmware update on SSD.
What brand/model system?

---

### Post by srkasdorf on 2018-08-27
Yeah I turned off fast startup through the control panel.  I just tried the command prompt method you linked above to turn off fast start up and it still only recognizes the flash drive.  I reloaded windows and chrome pulled up with my webpages so for some reason it is still not fully shutting down.  The computer I'm using is a dell xps9560-7001SLV-PUS, running windows 10.

---

### Post by oldfred on 2018-08-27
Dell needs both UEFI update & SSD firmware update.
Similar model Dells have same UEFI and issues.
Have you changed UEFI loading drives with AHCI, not RAID nor Intel SRT?
Install Windows ACHI drivers first before changing, but you can change back temporarily if needed to get back into Windows.

       DELL Inspiron 15 7000 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560) 
            Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488) 
    
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

---

### Post by srkasdorf on 2018-08-27
Quick update.  I updated the bios driver, and then went into boot menu and switched from RAID to AHCI.  The installation finally recognized the ssd space, and it went fully through the installation (install alongside windows).  It prompted me that I would have to restart the computer and when I tried to restart it froze up.  I hard rebooted and it now has the option to boot ubuntu in the boot menu.  When I load ubuntu it lets me click the sign in that I created but when I enter my password it freezes again.  Any advice?

---

### Post by oldfred on 2018-08-27
Are you using nomodeset boot parameter?
Most newer nVidia cards/chips need that to boot, then you install correct nVidia driver from Ubuntu repository or add the ppa to get the very newest driver if a very new card/chip.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL] If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by srkasdorf on 2018-08-28
Ok, I temporarily changed the boot parameter to nomodeset and was able to log in. I cleared the nvidia drivers and updated using sudo ubuntu-drivers autoinstall, and it installed the newest version of the nvidia driver. I restarted the computer, and it still won't load without changing the parameters to nomodeset. What am I missing?
I read somewhere that you have to go to system>software>additional drivers to change the driver to nvidia after installing, but there is no software tab in my settings menu.  Can't find it anywhere.  Is there anyway to change the drive from the command line after installation?

---

### Post by oldfred on 2018-08-28
Links above show command line install of nVidia. And if very newest driver needed, install of the ppa.
But if you install a different driver, you must uninstall/purge old one. Otherwise you get conflicts.

Use the commands in the first link to see what is installed.

Try Software Updater & then settings button.

---

### Post by srkasdorf on 2018-08-28
I had actually already tried all of that and It didn't work.  I just tried the exact same thing and just waited longer before restarting, and now it is recognizing the nvidia driver.  So I think I'm all good to go! Thanks a bunch for bearing with me on this, I know I had a lot of problems with this and I'm pretty new to all of it.
A few final questions about some of the settings.  I believe that now ubuntu will not load with the bios in RAID mode, but windows will not load with the bios in AHCI, I found a way to get around the AHCI and boot windows in this mode, but I don't know enough about the settings to know what impacts it has on the system.  Also I was wondering if I should keep secure boot and fast start up off or not.

---

### Post by oldfred on 2018-08-28
Never understood why some vendors are using a RAID mode with one drive. You should be able to install AHCI driver into Windows.

I turn off UEFI Secure Boot. Eventually we may need it. But currently it is more for control & marketing by Windows. You have a system well known for having virus, so what better than to market Secure Boot. The only thing is that Boot virus are not common. The main one was actually from Sony in trying to implement DRM on all music and that was BIOS, not UEFI.

If not changing system configuration, you probably can turn UEFI fast boot back on. That assumes no system changes and immediately boots. But you need to know how to get to UEFI if system has issues. Often cold boot. Both Windows & grub have menu settings to get into UEFI that works for most systems, but if neither boot?
You need to keep Windows fast start up off, unless you only want to boot from UEFI boot menu. Grub only boots working Windows. Note Windows will turn on fast start up with updates and abnormal shutdown may corrupt the NTFS, then needing chkdsk. Then grub will not boot Windows. You may be able to directly boot from UEFI, but best to make the Windows repair/recovery disk.

---


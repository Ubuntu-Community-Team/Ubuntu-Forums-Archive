---
title: "RAID intel rst, dual boot Win7 + 12.04.3. error: no such device"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by dan27 on 2013-08-29
Hi, 

I am an Absolute Beginner. 

Many failed installs led me to various forum posts indicating ubuntu *alternate* should probably be used with RAID 1.

This led me to download [Ubuntu 12.04.3 LTS (Precise Pangolin) 64-bit PC (AMD64) alternate install CD]("http://releases.ubuntu.com/precise/").

My system has [Intel® Rapid Storage Technology (Intel® RST)]("http://www.intel.com/p/en_US/support/highlights/sftwr-prod/imsm"). 

[Windows 7 USB/Download Tool]("http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool") and also [Pendrivelinux]("http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/") were both used to make a USB boot CD for Ubuntu.  Attempted installs resulted in the following message. 
> [!!] Load installer components from CD. 
 
There was problem reading data from the CD-ROM.  Please make sure it is in the drive.  If retrying does not work, you should check the integrity of your CD-ROM.  Failed to copy file from CD-ROM.  Retry?

THEN ...

I used MS Windows to burn a DVD with the [ubuntu-12.04.3-alternate-amd64.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.3-alternate-amd64.iso") file. 

I selected the following.
> Partitioning method:

Guided - use the largest continuous free space

Attempted installs finish and display these messages. 
>  
[!!] PAM configuration

Installation complete

Installation is complete, so it is time to boot into your system! Make sure to remove the installation media (CD-ROM, floppies), so that you boot into the new system rather than restarting the installation. 

error: no such device : 6ffe6d8f-a47c-4005-b763-1ee2c917c323

grub rescue> 

From 12.04.3 on a live USB CC I ran boot-repair.  

"Recommended Repair" button: [paste.ubuntu.com/6039358/]("http://paste.ubuntu.com/6039358/")

Then Windows 7 launched at boot. 

I again attempted another install and obtained the same results finishing in the "error: no such device" message and "grub rescue>" prompt. Back to live USB CD ...

"Create a boot info summary" button: [paste.ubuntu.com/6039049/]("http://paste.ubuntu.com/6039049/")
"Recommended Repair" button: [paste.ubuntu.com/6039066/]("http://paste.ubuntu.com/6039066/")

Again Windows 7 now launches at boot. 

***Despite the "Installation Complete" messages***, it seems there is no installed Ubuntu as unallocated space continues to display in Windows 7 Computer Management, GParted and Partition Wizard.

What should I do to launch an installed Ubuntu ?   ](*,)

---

### Post by lukeiamyourfather on 2013-08-29
I wouldn't touch Intel RST with a ten foot clown pole. It's nothing but trouble and in my opinion it's even less reliable than having no RAID. It can be done, use the forum search feature because this issue has been thoroughly covered before if you really want to use Intel RST.

---

### Post by oldfred on 2013-08-29
I agree with lukeiamyourfather that Intel SRT is the issue.

You have to remove the RAID meta-data from the drive. 
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

Since you have Windows 7, is it installed in BIOS mode or UEFI mode? Most Windows 7 systems were BIOS, but newer hardware had UEFI but Windows 7 still used the CSM/BIOS/Legacy setting to install & boot. But a few newer Windows 7 systems released just before Windows 8 used UEFI but without the secure boot that Windows 8 has.

---

### Post by dan27 on 2013-08-31
Thanks for your comments! 

Suggestion for Ubuntu team:  *"Installation complete" *messages should not display if installation is not complete!

dmraid commands removed the RAID **Volume **as displayed with the Intel **Matrix **Storage Manger (summary visible at every boot).  Then, installing Ubuntu also changed the Intel Matrix Storage Manager **Disk Type** for both disks to non-RAID.  Unfortunately, creating a RAID **Volume **through the Intel Matrix Storage Manger menu erases all content on both disks -- including the recently installed Ubuntu!    For me it was NOT possible to just "re-enable" RAID !!!

I was suspicious Intel **RST **was the problem, and was already considering giving it up.  I had already happily purge my two systems of all other Dell bloatware.  Your comments helped me happily get rid of Intel RST which was more important to me when the systems were new and I was running other programs.  Maybe someday I will run software RAID if needed.  

Rather than one computer with two 250GB disks and another with two 1TB disks, each computer now has one 250GB and one 1TB disk -- better for my backups.  One computer has Ubuntu, the other Windows, no dual boot. 
 
KISSS -- **K**eep **I**t **S**imple and **S**traight-forward **S**illy!

---


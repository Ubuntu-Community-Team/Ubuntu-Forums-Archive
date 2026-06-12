---
title: "Having trouble Dual Booting Ubuntu 12.4.2 with Windows 7"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Crimson Shadow on 2013-04-06
I have a Sony Vaio S Series (the newer 2012 model) it has an i7 processor, 12 GB ram, 640 GB HDD, 2 GB Nvidia Graphics Card, and Windows 7.I would like to dual boot Ubuntu with Windows. I tried to install Ubuntu 12.4.2 using a usb drive but when I get to the installation screen that is supposed to ask what type of installation I want, I encounter something unusual. The Installer doesn't see that I have Windows 7 installed on my hard drive and only asks if I want to "Erase everything on the hard drive and install Ubuntu" or "Something Else". I have run Boot-Repair, I clicked on recommended repair to see if that will solve the problem, it didn't. Boot-Repair changed the boot files of Windows and now the system will not boot into Windows 7. Boot-Repair also gave this URL [http://paste.ubuntu.com/5684061/](http://paste.ubuntu.com/5684061/). I mostly want to know if my computer can be salvaged from it's current configuration or if it is better to wipe the hard drive, reinstall Windows 7 and try again.

---

### Post by meijin3 on 2013-04-06
I had the problem with the Ubuntu installation disk not recognizing Windows before.. I'm not sure, but it may be because you have too many partitions. I deleted HP_Tools on my HP laptop and everything was dandy after that.

Edit: As far as not booting goes, you may have damaged your MBR (master boot record). This is just a guess on my part but I speak, again, from unfortunate experience. Try this perhaps? [http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

---

### Post by oldfred on 2013-04-06
You must have booted in BIOS/MBR mode, but your Windows 7 is installed in UEFI mode. So Boot-Repair installed a Windows boot loader into the MBR (not an issue), but also put a boot flag on the main Windows partition. IF BIOS that would be correct, but with UEFI and gpt partitioning the boot flag can only be on the efi partition. And you can only have one efi partition per drive.
Use gparted from liveCD, click on sda5, and right click to remove the boot flag.
From UEFI menu in UEFI mode you then should be able to boot Windows again.

Since you have a Windows 7 system, you do not have any of the secure boot issues.
Use Windows 7 Disk tools to shrink the Windows main install to make room for Ubuntu, but do not create any partitions as it may convert to dynamic which is not compatible with Linux.

Even though you do not have secure boot issues, it still is best to use newest installs that support that as they have the newest UEFI implementation.
       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by Crimson Shadow on 2013-04-06
> **oldfred said:**
> You must have booted in BIOS/MBR mode, but your Windows 7 is installed in UEFI mode. So Boot-Repair installed a Windows boot loader into the MBR (not an issue), but also put a boot flag on the main Windows partition. IF BIOS that would be correct, but with UEFI and gpt partitioning the boot flag can only be on the efi partition. And you can only have one efi partition per drive.
**Use gparted from liveCD, click on sda5, and right click to remove the boot flag.**
From UEFI menu in UEFI mode you then should be able to boot Windows again.

Since you have a Windows 7 system, you do not have any of the secure boot issues.
Use Windows 7 Disk tools to shrink the Windows main install to make room for Ubuntu, but do not create any partitions as it may convert to dynamic which is not compatible with Linux.

Even though you do not have secure boot issues, it still is best to use newest installs that support that as they have the newest UEFI implementation.
       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

How exactly do I do this? Sorry, I am new to partitoning hard drives, still learning.

---

### Post by oldfred on 2013-04-06
Only use Windows disk tools to shrink Windows but use gparted for everything else, from your live installer or download separate gparted liveCD.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by Crimson Shadow on 2013-04-06
> **oldfred said:**
> You must have booted in BIOS/MBR mode, but your Windows 7 is installed in UEFI mode. So Boot-Repair installed a Windows boot loader into the MBR (not an issue), but also put a boot flag on the main Windows partition. IF BIOS that would be correct, but with UEFI and gpt partitioning the boot flag can only be on the efi partition. And you can only have one efi partition per drive.
Use gparted from liveCD, click on sda5, and right click to remove the boot flag.
From UEFI menu in UEFI mode you then should be able to boot Windows again.



Search more forums and found out about more info on gparted. I did what you suggested and Windows still would not boot.

---

### Post by oldfred on 2013-04-06
Did you choose Windows from UEFI?

---

### Post by Crimson Shadow on 2013-04-06
> **oldfred said:**
> Did you choose Windows from UEFI?

Where would this menu be located?

 In my Bios I can only select whether or not to change from Legacy to UEFI. 

So am I correct to assume this is somewhere within Ubuntu?

---

### Post by oldfred on 2013-04-06
Newer BIOS that supported SATA had two entries. One was device order like hard drive, CD, floppy etc. And then under hard drive was boot order setting for each hard drive when you had more than one. Some had it as a sub-menu under device setting and others had it even on a different page.

UEFI is similar. You have a menu for devices and boot order of all the folders in efi partition. Some seem to now combine them all into one, others still have separate entries.
You may have to go into UEFI shell if you have that entry.

---

### Post by Crimson Shadow on 2013-04-06
> **oldfred said:**
> Newer BIOS that supported SATA had two entries. One was device order like hard drive, CD, floppy etc. And then under hard drive was boot order setting for each hard drive when you had more than one. Some had it as a sub-menu under device setting and others had it even on a different page.

UEFI is similar. You have a menu for devices and boot order of all the folders in efi partition. Some seem to now combine them all into one, others still have separate entries.
You may have to go into UEFI shell if you have that entry.


Sorry, I wish my system was that detailed but its not.

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by oldfred on 2013-04-07
I might check to see if Sony has an update to your UEFI/BIOS.

This user renamed some files to make it work.
 Sony Vaio dual UEFI boot with manual copy of files to efi partition
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

---

### Post by Crimson Shadow on 2013-04-08
> **oldfred said:**
> I might check to see if Sony has an update to your UEFI/BIOS.

This user renamed some files to make it work.
 Sony Vaio dual UEFI boot with manual copy of files to efi partition
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

I will try this soon.

I got tired of experimenting with the different solutions to fix the MBR and just did a system restore instead. 

Right now, I am going to shrink the size of the Windows Partition to make room for the Ubuntu install.

---

### Post by Crimson Shadow on 2013-04-13
Okay, there is a new problem. Well, I still have the problem of the Ubuntu Installer not recognizing that I have Windows 7 installed on my machine.

[ATTACH=CONFIG]241297[/ATTACH]

But now I get a new error when i choose "Something Else" for my installation type.
[ATTACH=CONFIG]241298[/ATTACH]

The Partition table doesn't even show up now.

The only thing that I have done is to shrink the volume size of Windows 7 to give room to the Ubuntu install. Here is what is my hard drive looks like on Gparted
[ATTACH=CONFIG]241300[/ATTACH]

I still just want to Dual boot Windows 7 with Ubuntu.

---

### Post by oldfred on 2013-04-13
Are you booting the 64 bit version in UEFI mode?
Did you turn RAID on at any point.
Does Windows need chkdsk? After any resize it needs chkdsk. Ubuntu will not work on hibernated or NTFS that needs chkdsk to prevent further damage.

---

### Post by Crimson Shadow on 2013-04-13
> **oldfred said:**
> Are you booting the 64 bit version in UEFI mode?

Yes

> Did you turn RAID on at any point.

No

> Does Windows need chkdsk? After any resize it needs chkdsk. Ubuntu will not work on hibernated or NTFS that needs chkdsk to prevent further damage.

I don't think so, I have booted windows several times without being prompted for chkdsk.

---

### Post by oldfred on 2013-04-13
Post this to see if it says anything.

 sudo parted /dev/sda unit s print

Did you create partitions with Windows? That often converts to dynamic partitions but also leaves meta-data on drive.
Or is this an Utrabook with Intel SRT? That uses RAID.

---

### Post by Crimson Shadow on 2013-04-13
> **oldfred said:**
> Post this to see if it says anything.

 sudo parted /dev/sda unit s print
[ATTACH=CONFIG]241304[/ATTACH]

> Did you create partitions with Windows? That often converts to dynamic partitions but also leaves meta-data on drive.
Or is this an Utrabook with Intel SRT? That uses RAID.

I shrunk the Windows partition using Windows Disk Manager, but I didn't create another partition. I figured the Ubuntu install would take the free space and create one for itself. 

This is not an Ultrabook but a regular notebok. It currently doesn't have a RAID configuration.

---

### Post by oldfred on 2013-04-14
If it is just text from the terminal you can copy & paste here. If long output use advanced mode and click on # to add code tags.

You have some gpt error which I have not seen.

You should download gdisk into liveCD and run it to see if it can parse the gpt table or its backup and/or fix the error.
sudo apt-get install gdisk

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)


 GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Crimson Shadow on 2013-04-14
> **oldfred said:**
> If it is just text from the terminal you can copy & paste here. If long output use advanced mode and click on # to add code tags.

You have some gpt error which I have not seen.

You should download gdisk into liveCD and run it to see if it can parse the gpt table or its backup and/or fix the error.
sudo apt-get install gdisk

The terminal was "unable to locate package gdisk"

---

### Post by oldfred on 2013-04-14
I do not have the ISO for 12.04.2 but booted Raring.
You can also down load the version from the rodbooks site and install it, but it is a bit more difficult.

```
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gdisk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 328 kB of archives.
After this operation, 755 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main gdisk amd64 0.8.5-1ubuntu2 [328 kB]
Fetched 328 kB in 1s (218 kB/s) 
Selecting previously unselected package gdisk.
(Reading database ... 160072 files and directories currently installed.)
Unpacking gdisk (from .../gdisk_0.8.5-1ubuntu2_amd64.deb) ...
Processing triggers for doc-base ...
Processing 32 changed doc-base files, 1 added doc-base file...
Processing triggers for man-db ...
Setting up gdisk (0.8.5-1ubuntu2) ...
ubuntu@ubuntu:~$
```

---

### Post by Crimson Shadow on 2013-04-14
How do I run the program?

I downloaded it from rodsbooks' website and installed it using the software center. Now I need to know the command to run the software gptfdisk.

Sorry for the dumb question, my knowlegde of Linux is still in it's infancy.

---

### Post by oldfred on 2013-04-14
It should just be this, but you have to give it commands. Did you read the instructions on the repair gpt link?
sudo gdisk /dev/sda

But as he says first, best to backup current data.
**sgdisk -b sda-backup.gpt /dev/sda**

Then he explains all the options.

---

### Post by Crimson Shadow on 2013-04-14
I have tried for the last hour or so trying to run gdisk with no luck. I have tried your commands and the website's commands. Do you have any other solutions?

---

### Post by oldfred on 2013-04-14
I have never seen that error. You could copy & paste the exact error into google and see what you get.

---


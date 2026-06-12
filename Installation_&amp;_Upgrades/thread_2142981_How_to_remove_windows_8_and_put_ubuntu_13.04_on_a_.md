---
title: "How to remove windows 8 and put ubuntu 13.04 on a sleekbook HP, somebody did it?"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by ajsalmeida17 on 2013-05-07
Hi everyone, a week ago i bought an sleekbook from HP, an envy 6, and it came with windows 8 and the UEFI boot. 
So, i really want to remove windows 8 and put ubuntu. I created an USB disk with ubuntu, and started the installation,
 but in the partitions menu, Gparted does'nt saw the partitions of HDD and also SDD. :confused: So , if somebody did it, please help me.

---

### Post by darkod on 2013-05-07
If the machine uses Intel RST with the ssd as caching disk, that setup is sort of a raid. That's why the installer doesn't show the disks correctly.

You need to disable the Intel RST option in windows (not sure if you need to do this since you are getting rid of windows).
Then go into bios and disable the Intel RST in there too. Also, change the SATA mode from RAID to AHCI.
If possible, and if you prefer, disable uefi boot too, it only creates problems and you don't lose anything by not using it. In HP the legacy boot option might be called CSM or similar I think.

After that you should be able to install ubuntu using the whole disk, using the auto method or manually.
If you are installing with manual partitioning, the disks might have gpt tables so you might need to set up a small 1MiB partition with no filesystem and with the bios_grub flag set (only for legacy boot). That is needed so that grub2 can be installed correctly on a gpt disk, and only applies for legacy boot. For uefi boot the bootloader files are on the efi partition.

---

### Post by oldfred on 2013-05-07
Darko prefers BIOS booting and just about everyone understands the BIOS boot install and repair procedures, where UEFI is new, and vendors are updating UEFI, Windows is makeing fixes & Linux is trying to update its UEFI to work with secure boot.

I might leave an efi partition of 250 to 300MB FAT32 as the first partition even if installing in BIOS/CSM/Legacy mode. Then in the future you could convert to UEFI when it is a bit easier or more understood. The efi partition is supposed to be first and later it would be difficult to add, and is not a large part of a drive.

If just installing Ubuntu you should be able to turn secure boot off and fast boot setting off and just install in UEFI mode. How you boot installer flash drive, either UEFI or BIOS is how it installs. 

Since it is an Ultrabook you have the Intel RAID issue and you will have video issues with the dual video. nVidia just last week released the first Linux driver that works with Optimus, but it may need the kernel in 13.10. Most have been using Bumblebee with success.

How large is SSD. Many install just / (root) to SSD for quick boot and then install /home or data partitions onto the hard drive.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

      
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

While Lenovo, has some good info on settings for installing with Intel, nVidia dual video.

 [http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by darkod on 2013-05-07
Yeah I forgot, you need to remove the meta data from both disks using the dmraid commands oldfred posted. This is to remove the traces of the setup because the installer might still consider the disks as part of raid.

---

### Post by ajsalmeida17 on 2013-05-07
Ok, but it is an radeon graphics, so .. i think that there's no problem, i will stop the intel SRT and try to install again looking at the post of envy 6.

---

### Post by ajsalmeida17 on 2013-05-07
One more question.. It will work if i just select the one partition of 225 MB FAT32 that already exists, as efi partition?? And delect the windows partitions, and after use this partitions to ubuntu?

---

### Post by oldfred on 2013-05-07
Yes, you can only have one efi partition per hard drive.

I always hesitate to remove Windows. You have paid for it. And we  get users who come back and have one app or game that they cannot live without and then want Windows back.

---

### Post by ajsalmeida17 on 2013-05-08
Well, i think that i not need windows anymore, and and will use this machine to tests with network, running 7, 8 virtual machines i choose ubuntu just because it have more suport
to some devices.
I will try to install one more time
thank you

---

### Post by ajsalmeida17 on 2013-05-08
I tried to install, select in instalation  of ubuntu. The partition efi , i marked as an boot efi patition and then used another partition as /. But when i starts the 
computer, ubuntu does'nt run. Should i anable the SRT ?

---

### Post by oldfred on 2013-05-08
SRT is a Windows function. If you have removed Windows you may want to install root to the SSD to have Ubuntu boot quickly.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by darkod on 2013-05-08
I will say again, use the legacy boot. :)

Did you make sure you booted the install media in uefi mode? I guess you did, since it asked you to specify the efi partition.

Your bios/uefi manager might need you to create the boot entry manually.

---

### Post by oldfred on 2013-05-08
If you do not have a bios_grub partition, Boot-Repair may only want to repair in UEFI mode. 
You need a 1MB unformatted partition anywhere on drive. Right click in gparted manage flags and add bios_grub. Then grub-pc can correctly install to protective MBR of the gpt drive. Boot-Repair should offer with check options to repair either way, but will primarily choose the method you boot the liveCD/DVD/Flash or if you boot repair in BIOS it will try to repair in BIOS but may have check box for efi, or if booted in efi mode will try to repair in UEFI mode.


And then you have to have UEFI/BIOS set to boot in BIOS/CSM/Legacy mode. If you want to boot in BIOS mode.

---


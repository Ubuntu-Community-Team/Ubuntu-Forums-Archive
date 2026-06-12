---
title: "BIOS Changes for a Windows 10 Laptop"
date: 2018-08-16
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2018-08-16
Hi -

Can you please guide me as how I can install Ubuntu, without disturbing Windows 10 ( as it's needed for my kid ) ?

[B]Current BIOS Settings

Boot Mode : UEFI
Secure Boot : ON

[/B]UEFI Options
--Windows Boot Manager
Others
--BIOS Setup
--Diagnostics
--Change Boot Mode Settings**
--BIOS Flast Update

**Change Boot Mode Settings has the following
--Legacy Boot Mode: Security Boot off
--UEFI Boot Mode : Security Boot off

I have Ubuntu installer in a USB drive and when the laptop boots up, if I do F12 it shows up the USB drive, from which I can fire the installer.

My Disk Layout is attached. 195GB is the space I'm planning to allocate for Ubuntu.

**Questions**
[LIST=1]
[*]Do I need to change any setting in my BIOS ?
[*]Can I proceed with the installer to point to the disk and continue the installation - I don't have mess up Windows 10 ?
[/LIST]

Thanks.

[ATTACH=CONFIG]280762[/ATTACH]

---

### Post by oldfred on 2018-08-16
What brand/model system? What video card/chip?

I have  5 or 10 UEFI settings I change, some required, others optional.
Best to have UEFI secure boot off, UEFI fast boot off, USB full support or allow boot. Several of those are multiple settings in various places.

You probably need to update UEFI from vendor and if SSD update firmware.

If you used Windows tools to shrink NTFS partition that is good, and reboot so it can run chkdsk.
Make sure Windows fast start up is off. That is different that UEFI fast boot. And Windows will turn fast start up back on with updates which you may not see as in back ground.

See 9 "easy" steps to install Ubuntu in link in my signature and lots more info on UEFI install and repairs.

---

### Post by shankariyer on 2018-08-17
Dell Inspiron 15-3565

Processor : AMD A9-9400 RADEON R5, 5 COMPUTE CORES 2C+3G   [Cores 2] [Logical/Core 1]

This laptop doesn't have SSD, but spindle based HDD.

On the disk layout - I can see only the 195GB chunk is free... rest seem to have been blocked by Dell for recovery and other utilities.

---

### Post by yancek on 2018-08-17
I would suggest that you start by reading the Ubuntu documentation on dual booting UEFI with windows, see the link below.  You have unallocated space so that's a good start and follow the suggestions by oldfred above to run chkdsk from windows before you start.  Also, the fastboot/hibernate and other suggestions from the Ubuntu link.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-08-17
My one Windows system is a Dell Inspiron-3647. I have Windows only for Comcast DRM which still uses flash. Once I changed some settings in UEFI, it installed without issue. New Dells have to have other settings changed. Very new Dell may need updated drivers, also. Not sure what your exact configuration is.

       Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

---

### Post by shankariyer on 2018-08-17
Thanks @oldfred... My configuration would be this... [https://www.gadgetsnow.com/laptops/Dell-Inspiron-15-3565-A561226SIN9-Laptop-AMD-Dual-Core-A96-GB1-TBWindows-10](https://www.gadgetsnow.com/laptops/Dell-Inspiron-15-3565-A561226SIN9-Laptop-AMD-Dual-Core-A96-GB1-TBWindows-10)
( if that link doesn't work, you may try this [https://www.flipkart.com/dell-inspiron-15-3000-apu-dual-core-a9-6-gb-1-tb-hdd-windows-10-home-3565-laptop/p/itmf3s3f6hgstnfk](https://www.flipkart.com/dell-inspiron-15-3000-apu-dual-core-a9-6-gb-1-tb-hdd-windows-10-home-3565-laptop/p/itmf3s3f6hgstnfk) )

---

### Post by oldfred on 2018-08-17
I do not know the AMD versions as well. Not sure if any specific issues with those that are different than the Intel versions.

are you sure Windows fast start up is off. And drive is set for AHCI in UEFI. If still RAID or Intel SRT then add AHCI driver to Windows before changing setting in UEFI.

If Windows still not seen, you can only install Ubuntu using Something else, so it only installs to partitions you create. You can create partition(s) in advance with gparted or during install.
Default install is / (root). It now creates swap file, so separate swap partition not required. And it will use an existing ESP - efi system partition and correctly share that with Windows. Since allocating larger space I might use separate /home partition. If partitioning in advance create a 25 to 30GB ext4 partition for / and rest as ext4 for /home. You have to use Something Else and choose (change button) which partition is / and which is /home. 

Be sure to fully backup Windows and create a Windows repair flash drive.
When my Dell was new it wanted a Dell backup, a Windows backup & I made a full image backup with Macrium Reflect. That took 3 days as I had to go to store & buy more flash drives. But after partitioning in advance & booting Ubuntu live installer to install Ubuntu, it only took about 10 minutes for working install.

       UEFI install  Windows 10
[https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi)
UEFI install,windows 8 with Something Else screen shots
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[URL="http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html"]http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html

      [/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html"]
[/URL]

---


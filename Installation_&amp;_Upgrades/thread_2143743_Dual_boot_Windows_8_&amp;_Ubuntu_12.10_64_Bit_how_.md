---
title: "Dual boot Windows 8 &amp; Ubuntu 12.10 64 Bit how to proceed"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by keevill on 2013-05-09
I have made a new post for this problem .

I have been trying to install Windows 8 and Ubuntu 12.10 ( 64 Bit ) on a Lenovo twist notebook. I have now installed Windows 8 ( Non secure boot non UEFI ) and I am following the instructions in the post below.

[http://askubuntu.com/questions/280673/ubuntu-12-10-installer-doesnt-recognise-windows-8-partition-on-toshiba-c850-lap](http://askubuntu.com/questions/280673/ubuntu-12-10-installer-doesnt-recognise-windows-8-partition-on-toshiba-c850-lap)

The problem is that Ubuntu doesn't recognise that windows is installed and if I ignore this, and proceed by selecting 'other' and go on to partition the free space on the hard disk for Ubuntu, I lose the Windows boot when it's completed. Using Boot Repair doesn't work either so I have to clear it all off using Gparted and start over by installing Windows 8 again. What do I have to do to get the Windows install recognised and then on to install Ubuntu ? Thanks,

---

### Post by fantab on 2013-05-10
Can you tell us what partitioning scheme you are using? I want to know if you are using legacy 'msdos' partition table or latest 'GPT'? Because with GPT you will need 1 MB bios_grub partition- no format - to boot in Legacy BIOS mode.

---

### Post by keevill on 2013-05-10
> **fantab said:**
> Can you tell us what partitioning scheme you are using? I want to know if you are using legacy 'msdos' partition table or latest 'GPT'? Because with GPT you will need 1 MB bios_grub partition- no format - to boot in Legacy BIOS mode.

What is the best way for me to find out in order to tell you?
Thx,

---

### Post by fantab on 2013-05-10
Run Gparted from Ubuntu LiveDVD/USB and VIEW -> Device information. This will open a pane on letf-hand side and you can check and confirm "Partition Table".


[ATTACH=CONFIG]242412[/ATTACH]

---

### Post by keevill on 2013-05-10
[ATTACH=CONFIG]242413[/ATTACH]/dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it
should.  Perhaps it was corrupted -- possibly by a program that
doesn't understand GPT partition tables.  Or perhaps you deleted the
GPT table, and are now using an msdos partition table.  Is this a GPT
partition table?

---

### Post by fantab on 2013-05-10
Yes, you have a GPT table. You have two options:

1. Use GPT: Windows will not install to GPT without UEFI, Ubuntu can. But both OS should be in same mode, either both should be UEFI or both 'Legacy'.
2. Use MSDOS: You can install both OS in non-UEFI mode. 

Choose.

If you ask me then I'd say GPT and UEFI are the future but since they are new there are issues and we are still figuring out how they work.
MSDOS and legacy BIOS are easy compartively, we KNOW how they work and they are not going anywhere at least for another 5-6years.

---

### Post by keevill on 2013-05-10
Please can you give me some instructions how to go with the MSDOS and legacy BIOS route.
I have no idea how to proceed right now with this.
Thank you.
-keevill-

---

### Post by fantab on 2013-05-10
Disclaimer: I have not installed Windows8 in legacy mode so I don't know if it works. In all probablity it should install on 'msdos'

Using GParted from Ubuntu LiveDVD/USB change the partition table to "msdos" by selecting 'Device'-> 'create new partition table'. Default will be 'msdos' but double check using 'advanced'. Done. DO NOT create partitions. Exit Gparted. 
Install and run '[FIXPARTS]("http://www.rodsbooks.com/fixparts/")' this will remove any GPT residue/leftover from the HDD. Shut Down your computer.

Boot with Windows Install Disk. Create partition C: of approx. size 70GB or more. If you need another partition to share DATA between Windows and Ubuntu then create one of about 100GB. Leave rest of the space on HDD as unallocated. Install Windows 8. Confirm it boots by restarting a couple of times.

Boot with Ubuntu LiveDVD/USB, "Try UBUNTU", Run Gparted and partition your HDD for Ubuntu:

Note: with 'msdos' partition table you can ONLY have FOUR Primary partitions (I assume that you have created two primary NTFS partitions during Windows Install) so we will have to make the fourth partition as EXTENDED. Extended partition is a Primary Partition which contain several LOGICAL Partitions. This is how we by pass the 4 primary partition limit on 'msdos' table.

From the 'unallocted' space create:
25GB PRIMARY partition, Formatted with EXT4
All the Remaining GB EXTENDED (after this you will have the equal amout of 'unallocated space')
25GB LOGICAL partition, Formatted with EXT4 (Just in case you want to install another flavor/version of Ubuntu or another Distro)
2-4GB LOGICAL SWAP
Remaining GB LOGICAL EXT4.

Done. Exit Gparted.

From Desktop or Launcher "Install UBUNTU".

At the appropriate Screen/Dialog which says "Installation Type" choose "SOMETHING ELSE". This will take you to the next Dialog where you can choose partitions to install

Select the first 25GB ext4 formatted partition and hit 'Change', use "/" to install Ubuntu.
Select the last partition, hit 'Change', and use '/home' 

Thats it. continue with installation.

---

### Post by oldfred on 2013-05-10
When you install Windows over a gpt drive to boot in BIOS mode with MBR(msdos) it converts gpt to MBR. But it only overwrites the primary gpt partition table. One advantage of gpt is that is also has a backup gpt partition table at end of drive and Windows seems to ignore it. But LInux tools see both MBR and gpt and get confused.

If you want MBR you have to remove backup gpt partition table with fixparts.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

I missed that fantab already posted that your need fixparts.

---

### Post by EricKit on 2013-07-08
Hello, if you are still here.. I know it's been a while, but I have installed Ubuntu 12.10 on my Lenovo Twist.  I kept UEFI on, but had to disable secure-boot to get it to boot windows from GRUB.  All I did was make a USB live key from the daily builds.  I also made some free space from my Windows partition using the Windows Disk Manager under Admin Tools -> Computer management.  When I booted to the keyI said I want to install Ubuntu.  *To get your wifi to work you have to use 3rd party drivers from the update center, not needed for install though I just wired it for that since it was having issues with the wifi card* To install It did not recognize any Windows being installed so I chose the "Do something else" option.

I installed by creating 4 partitions, all were primary partitions since I am using UEFI.  If you are not you will end up with Logical Paritions.
Mount - Size - FileSystem
/ - 15 GB - EXT4
/home - As much as you need, this isn't even necessary, just nice if you want to reinstall Ubuntu without losing your data - EXT4
/boot - 250 MB - EXT2
Swap - 8GB - SWAP

I chose these sizes kind of randomly, do what you think is right here, the SWAP should be bigger than your RAM.  I used the SwapFaq here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) to help me out.  I also didn't make my home foler too big because I redirected my pictures/videos/documents folders to the Windows drive and made a script to mount that drive on boot.

After making the paritions it should install just fine!  GRUB detected a bunch of Windows installs and I used Grub Customizer to remove all the ones I don't want (because some are EFI and some are not) but I kept booting in UEFI without an issue.  Even Ubuntu boots using secureboot, just Windows won't.

Also if you can't find your windows Install with GRUB, just hit enter when it's booting, then F12 to select a boot drive, and pick your Windows one and it will boot without going to GRUB.  This worked even with Secure Boot on.

---

### Post by fantab on 2013-07-08
Glad that you are successfully dual-booting Windows and Ubuntu.

Just a suggestions: with only 15GB for '/' you may run out of space it unused kernels pile on. 20-30GB is good. 20gb is safe and 30gb is plenty. Also SWAP of about 2GB is plenty if you have 4GB or more of RAM. Only if you 'Hibernate' your Ubuntu that you need RAM equal to or more than your RAM in GiB, not GB.

Otherwise its all good.

--Regards.

---


---
title: "Expand extended partition to install 2nd distro"
date: 2019-06-08
forum: Installation &amp; Upgrades
---

### Post by Ogden on 2019-06-08
I currently have Ubuntu Mate 16.04 installed (legacy BIOS) and want to add a second distro, possibly Xubuntu.  My current hard drive setup:

      Device ------     Boot         Size    Type
>>  /dev/sda1   *       28G --  Linux
    /dev/sda2    ------- 96.9G   Extended
    &#9500;&#9472;/dev/sda5    ---- 93.1G  Linux
    &#9492;&#9472;/dev/sda6        ------ 3.7G  Linux swap / Sol
    Free space    --------- 341G

Mate is installed in a contiguous space at the front of the drive.  Free space is at the end.

Q1- I want to reserve some of the free space for a third distro if I ever need it so ... do I just expand the extended partition by ~120 gig using GParted and install Xubuntu /root and /home in the 120 gig?

Q2- When expanding the extended, will it show 120 gig of free space inside the extended and 221 gig free space outside?

Q3- Can I assume the Mate swap will be used by Xubuntu?

Q4- When I install Xubuntu and install Grub on /dev/sda, should it update the Grub from Mate for a dual boot or do I have to run update-grub from the live installer?

---

### Post by oldfred on 2019-06-08
New installs use swap file, but if you have a swap partition, it will use that.
Some have had issues where swap partition was reformatted and then fstab in older install has wrong UUID making for very slow boot as it has to time out. Check UUID after install.
I installed with swap file, by telling installer not to use swap partition.

Do not share /home. But you can create one larger data partition and use that in all your installs. I also move Firefox & Thunderbird profiles to shared data so very little mostly hidden settings are left in /home folder.

Last install will be the version of grub in MBR if BIOS or default in UEFI if UEFI. You can boot into your main working install and reinstall grub to make that grub default. Note that major updates in newer install may reinstall grub and change which boots first again. 

I now only use gpt, so do not have extended partition. Back when still using MBR, I typically made rest of drive as part of extended, but did not allocate all of drive to partitions.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 

      
 If you do not want grub installed from live installer:
sudo ubiquity -b
Then update grub in main working install to find new install & add it to grub menu.
[http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527](http://askubuntu.com/questions/838450/how-can-ubiquity-be-forced-not-to-install-grub/838527#838527)

If BIOS, you can reset grub's memory on where to install, and tell it not to reinstall at all.
       
 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---


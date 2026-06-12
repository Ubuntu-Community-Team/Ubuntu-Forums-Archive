---
title: "Need to dual boot Windows 7 &amp; Ubuntu 13.10"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by nemesis045 on 2014-02-11
Hi all,

I know this is a very frequently asked question but hear me out here. Most tutorials assume you have a windows installation already and some of these are using the older Fat32 & ext2 partitions.

I have Ubuntu 13.04 32-bit currently installed on my system. The system has a Dell Windows recovery partion of ~16GB size (this came with my Dell Laptop) and a larger partition of ~285 GB, where the ubuntu 13.04 is currently installed. I am looking forward to end up with a **dual boot** of **Windows 7 Professional 64-bit **and **Ubuntu 13.10 64-bit**, preserving the **Dell Recovery partition** and using a large **Partition for Data**. From what I read, I think I might prefer clean installs for both OS's.

I'm a bit of a newbie to Linux as well, which I installed after a recent hard drive crash.
 
I was hoping if you could help me with the scheduling the steps/tasks I'd need to perform to achieve this dual boot.

I am looking for basic specific information on:
What programs to use in order to repartition the hard drive before I install any OS, considering I have Ubuntu already installed.
What size of partitions would you recommend for Windows 7 Professional OS and Ubuntu 13.10 OS. I think I'll use a larger separate partition for data, in case either OS crashes. What about  Linux Swap size?
What formats are best for the above mentioned OS's? Ext3,EXT4,NTFS,FAT32,etc.?
Once repartitioned what order would you recommend installing the OS. If I'm not mistaken, most believe Windows comes first.
Are there any steps I need to take in between the installation setups of the two OS's?
What are the pros/cons of letting the Windows Boot Loader / GRUB loader be primary? How do  make the better one primary? Do I do this after I install both OS's?
Any other critical issues that I may have overlooked that I would need to address during this process of setting up the dual boot?

I am looking for general directions and guidelines.

Any input is much appreciated.

---

### Post by sudodus on 2014-02-11
> **nemesis045 said:**
> 
I am looking for basic specific information on:
What programs to use in order to repartition the hard drive before I install any OS, considering I have Ubuntu already installed.

Boot from an external CD/DVD/USB drive and run ***gparted*** (it comes with the Ubuntu desktop iso file). When you have the chance, avoid UEFI. If you have to use UEFI, you must also use the GUID partition table (GPT).
> 
What size of partitions would you recommend for Windows 7 Professional OS and Ubuntu 13.10 OS. I think I'll use a larger separate partition for data, in case either OS crashes. What about  Linux Swap size?

If you are good at putting data into a separate partition, Ubuntu can be into only 12 GB, but I would recommend at least 20 GB. Windows needs more, maybe 50 GB. Linux swap should be slightly more than RAM (in gibibytes) if you plan to hibernate. Otherwise 1 GB is probably enough.
> 
What formats are best for the above mentioned OS's? Ext3,EXT4,NTFS,FAT32,etc.?

I recommend what is standard for Ubuntu: ext4 for the root partition, and NTFS for the common data partition (as well as for Windows).
> 
Once repartitioned what order would you recommend installing the OS. If I'm not mistaken, most believe Windows comes first.
Are there any steps I need to take in between the installation setups of the two OS's?

Yes, install the least intelligent system first ;-) If you have already made the partitions, it should work smoothly.
> 
What are the pros/cons of letting the Windows Boot Loader / GRUB loader be primary? How do  make the better one primary? Do I do this after I install both OS's?

I prefer grub, and it will be there, if you install Ubuntu after Windows. Install it to the head of the drive (not to a partition), for example /dev/sda (no digit).
> 
Any other critical issues that I may have overlooked that I would need to address during this process of setting up the dual boot?


Start with a ***backup*** because editing partitions and installing operating systems can go wrong. You may even destroy the recovery partition. Clonezilla can make an image of the drive when it contains only the recovery partition and the current Ubuntu system. Use an external drive to store the image.

---

### Post by oldfred on 2014-02-11
In addition to sudodus' good suggestions.

Have you installed a lot of apps in your 32 bit install? You may want to export a list to reinstall the 64 bit versions.
And backup /home as that has your settings for all applications and your data.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Windows 7 default install is two primary partitions, one 100MB boot partition, so you can encrypt main install. If not encrypting Windows you can install in one primary NTFS partition with the boot flag. Linux works just fine from logical partitions and Windows will read the NTFS data partition if logical, so all other partitions can be logical. Only Windows boot has to be primary.
You can create the NTFS partition with gparted and add boot flag. Window will not install without boot flag. some have reported they had to reformat again as part of install of Windows. Only use Windows partition tools to resize Windows if necessary and always reboot Windows after any NTFS partition size change, so it can run chkdsk and make other fixes.

I always prefer to manually partition with gparted and then use Something else to install choosing partitions to use, formats etc. But you have to understand partitioning and have a good partition plan on sizes in advance.

---


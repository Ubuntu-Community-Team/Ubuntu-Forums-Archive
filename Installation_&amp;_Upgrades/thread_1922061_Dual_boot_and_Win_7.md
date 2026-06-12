---
title: "Dual boot and Win 7"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by schizovivek on 2012-02-07
hi... i know this conversation is ubuntu wiv vista but im having a similar problem with win 7 and ubuntu 11.

Win 7 was working fine. There are no space issues in the drive where Ubuntu and WIn7 are installed (there was 50 odd gb free space of which i allocated 10 to Ubuntu). Now the problem is. Ubuntu boots wivout any issues, but when i enter the Windows 7 mode it goes blank and then comes back to the boot menu. The worst part is that I am not able to get my bootable Win 7 dvd to run either. At the prompt that says press any key to boot from dvd, i press the key and it still gives me the Ubuntu bootloader screen !

any help would be greatly appreciated. I wanna have a dual boot coz i wanna learn more about Ubuntu but I have free lancing work and other imp setups in my Win 7 that i just cant afford to lose. 

Note: for ppl who say setup everythin into Ubuntu, realize for me bandwidth is a constraint.. this is another topic altogether though :D

---

### Post by bcbc on 2012-02-07
> **schizovivek said:**
> hi... i know this conversation is ubuntu wiv vista but im having a similar problem with win 7 and ubuntu 11.

Win 7 was working fine. There are no space issues in the drive where Ubuntu and WIn7 are installed (there was 50 odd gb free space of which i allocated 10 to Ubuntu). Now the problem is. Ubuntu boots wivout any issues, but when i enter the Windows 7 mode it goes blank and then comes back to the boot menu. The worst part is that I am not able to get my bootable Win 7 dvd to run either. At the prompt that says press any key to boot from dvd, i press the key and it still gives me the Ubuntu bootloader screen !

any help would be greatly appreciated. I wanna have a dual boot coz i wanna learn more about Ubuntu but I have free lancing work and other imp setups in my Win 7 that i just cant afford to lose. 

Note: for ppl who say setup everythin into Ubuntu, realize for me bandwidth is a constraint.. this is another topic altogether though :D
Please run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Thanks

PS I'm going to flag this for a separate thread. It's best not to mix threads. Thanks

---

### Post by Mark Phelps on 2012-02-08
You can try using Boot-Repair to see if it can restore Win7 boot capability:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by schizovivek on 2012-02-08
@bcbc

i ran the boot info script.. cant make heads or tails of it :$ .. so as said in the download page of the script im attaching the results.txt file link here.

[https://docs.google.com/document/d/1fJaa4JhLkY6yNiufsyJLNK4nmsFUq7B6K0K_L2iDzGk/edit](https://docs.google.com/document/d/1fJaa4JhLkY6yNiufsyJLNK4nmsFUq7B6K0K_L2iDzGk/edit)

Edit:

@Mark Phelps

I'm trying boot repair now.. will post once its done with the results

---

### Post by oldfred on 2012-02-08
Did you copy partitions. You have a bunch of size issues that corrupt the system.

You sda1 which is the Windows boot/repair partition has grub2's boot loader installed to it. Windows NTFS partitions have to have a NTFS boot signature not grub. 

NTFS keeps a backup and this can restore from the backup if it is still ok.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Your other issues on partitions beyond the end of the drive in sdb or not in extended partition in sdc may need this:

First back up both sdb & sdc with this:

First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts_sdX.txt

Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by bcbc on 2012-02-08
+1 to what oldfred said. 

Grub in the bootsector of /dev/sda1 is what's preventing windows from booting. Grub should be installed in the drive MBR  (/dev/sda), not the partition /dev/sda1. So that link to repair the bootsector is what is required. But that will stop Ubuntu from booting as well, so you should boot Ubuntu first and run:
```
sudo grub-install /dev/sda
```Then install and run testdisk to recover the /dev/sda1 bootsector:
```
sudo apt-get install testdisk
```and follow instructions [in the link oldfred provided]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

But that doesn't answer all those partition table exceptions. Follow oldfred's advice for that afterwards. Make sure you backup important data first: partitioning always carries a small risk.

---

### Post by schizovivek on 2012-02-09
hey guys.. thanks for the help... im not really able to do everything u have advised due to a time crunch [12-14 hrs in off does tht to a man :(] .. i did try the boot repair.. that dint work..
also.. the reason i think u are seeing so many partition related inconsistencies coz in Win 7 i had encrypted 2 partitions with bitlocker (i have total 3 hdd connected. 1 500gb sata and 2 1tb usb drives)... before i try the solution provided by bcbc and oldfred i ran the boot info script again wthout any of the drives connected (Except the 500 gb sata which had the win 7 loaded)..

i would appreciate it if u could hv a look at the new results.txt file and let me know if i shud proceed wiv ur testdisk solution..

[https://docs.google.com/document/d/1zbIuVpQ96DpgqFNuYIvDbE0dA44vUQ97Mjn-0LEJdWM/edit](https://docs.google.com/document/d/1zbIuVpQ96DpgqFNuYIvDbE0dA44vUQ97Mjn-0LEJdWM/edit)

i apologize for bein a pain and pardon me for being a noob but im looking into linux after around 7 yrs :$ (ive forgotten everything !)

---

### Post by oldfred on 2012-02-09
The testdisk will just try to recover the PBR or boot sector of the Windows partition.

Does Ubuntu boot ok.

Not sure what encryption might have done to partitions on other drives, but partition table cannot have illegal/invalid entries.

---

### Post by schizovivek on 2012-02-10
yup .. ubuntu loads fine.. 
i dld'd testdisk 6.13 for linux.. extracted it.. when i run the command
sudo testdisk_static  .. it says command not found. (im already on the folder where that file is)

used ubuntu software center to install testdisk, but dunno whr its installed and how to use it.. finally im installing wine since i had the exe version of testdisk from long b4

in the meanwhile any pointers as to why its not running?

Edit:
got it to work using the command sudo ./testdisk_static  .. will get back to you on the progress

---


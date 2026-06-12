---
title: "Changing default drive for installation Ubuntu 14.04 alongside Windows"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by sbmorton on 2016-01-06
Hi, 

I'm trying to install Ubuntu 14.04 on my 'spare' PC that already has Win 7 and Win XP on it and several disk drives (Win7 system, WinXP system, a Raid 0 array and a Raid 1 mirror). What I want to do is use the free space on the WinXP system drive - it has about 40GB free, and I'm aiming to give 30 GB to Ubuntu [I only need a 'play' system to try out] - but the installer pre-selects the Win7 drive which has 45 GB free and the 'Select drive' dropdown doesn't offer any alternative to choose, even though the Ubuntu partition default is only 27.4 GB and all the other drives have at least that much free.

So my question is: is there some way I can control what drive is chosen for the default installation? or is there some other way to achieve this?
I've looked for this in the installation doc and wiki but everything seems to either be from older releases or assumes you'll go with the default or else completely plan your device/partition/mountpoint allocations from scratch - and I'm hoping to save myself that effort ;)

Apologies if I've missed something obvious, the last time I tried Ubuntu was release 10 and the WUBI installer was simpler then, if more primitive!

BTW, if I run Ubuntu Live from the DVD it does see all my disks, including the WinXP drive, so I know it's not a device recognition issue.

Any advice welcome! (if all else fails I'll bite the bullet and make a full allocaton plan...)

Thanks
Steve

---

### Post by yancek on 2016-01-06
I would suggest you select the "Something Else" option for Installation Type as it will give you more control.  The Install Alongside option is basically an auto install and you won't have a clue if something goes wrong.  I'd also suggest you read the link below which explains in detail installing Ubuntu as well as dual-booting further down the page.  Additionally, it also has a lot of valuable information on some of the basics of Linux partitioning.


[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

If you just want to test Ubuntu, you might be better off just trying it from the DVD or flash drive you are using or installing it in Virtualbox or some other virtual software installed on windows.  Do you have a windows installation DVD?  The default with any operating system is to install it's boot loader to the Master boot record of the first drive.  If you do this with Ubuntu and it installs it's boot code to the MBR and you later decide you don't want to keep it, you will not be able to boot windows without putting it's code in the MBR and the best way to do that is with the windows installation DVD using the repair option.

A standard windows system will not be able to boot any Linux system although you might get third party software to do that.

---

### Post by sbmorton on 2016-01-07
Thanks Yancek, that link is very useful for some planning details - but  it looks like I'll have to do a partition plan after all <sigh>
Ah well, it will be educational...

I  should have said that I'm not completely new to Linux/Unix (I've used  those on and off for 20 years at customer sites) but my skills are a bit  rusty after a few years mainly on Windows sites, so I'm setting up  Ubuntu as a refresher for me and longer term to assess it for a move  away from Windows when I retire in a year or two. Hence I'd prefer an  installed system to running from the DVD to get more 'normal'  performance and install additional software.

One complication for  me is that I need to be able to boot Ubuntu, Win 7 or Win XP when I  finish but I'm confident the Linux bootloader will do that, provided I  don't screw up the configuration! At least I do have original  installation media for everything if 'repair' is required.

cheers
Steve

---

### Post by oldfred on 2016-01-07
You want to be sure to use Something Else if you have more than one drive or install.
Only with Something Else do you get to choose which drive the grub2 boot loader is installed into, and you want it on the same drive as your Ubuntu install, and leave Windows boot loaders on the other drives. But Windows may only be booting from one drive anyway, as its default boot is drive set in BIOS as boot and partition on that drive with boot flag. You may have Windows 7 boot files in XP install's partition.

You may need to install RAID drivers after you have installed to be able to mount your RAID arrays.

While I prefer to use gparted to partition in advance, you can just use installer to create a / (root) as ext4 and swap with 2GB of space in the unallocated. With MBR, you do have the 4 primary partition limit, so you need at least one primary left as the extended to hold the logical partitions. Or the unallocated needs to be in the extended if you already have one.

Several more links with screen shots, but all are about the same as the one posted above by yancek, which is a good example.
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---


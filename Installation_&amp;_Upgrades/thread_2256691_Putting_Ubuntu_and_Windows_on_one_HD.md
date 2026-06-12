---
title: "Putting Ubuntu and Windows on one HD"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by John_Combe on 2014-12-14
My mother's laptop had its hard drive die and while she does not have the replacement HD yet she wants to know how to install Windows 7 and Ubuntu onto the same hard drive.  Do I setup Windows 7 first and when its finished put in the Ubuntu 14.04 install disc into the dvd drive and use wubi to install along side Windows 7? Do I create separate partitions, if so how do I do it so the two would not interfere with each other as my mother wants two drastically different operating systems which are optimized for different file systems on one HD.
    The laptop has intel integrated graphics and is at least a duel core system, uses a SATA hd controller (the failed HD was a SATA 3 interface type) and has enough ram for both operating systems, I do not have the specifics but it does meet the minimum requirements for both at the very least.
    In any case what has to be done in a step by step, generalized order since the replacement HD is not here but my mother wants the information to create a fresh duel boot system hard drive before work is started. If I have questions later about what is typed I will post them as needed.

---

### Post by Mark Phelps on 2014-12-14
> Do I setup Windows 7 first  Yes

> and when its finished put in the Ubuntu 14.04 install disc into the dvd drive and use wubi to install along side Windows 7?NO, do NOT use Wubi.  It has been discontinued and is no longer supported.

> Do I create separate partitions, yes

> if so how do I do it so the two would not interfere with each other

Would suggest the following process:
1) Boot from the Ubuntu install media, select Try Ubuntu, when you finally get to a desktop, run GParted (Gnome Partition Editor).  Use that to create a 30GB NTFS partition on the drive.  This will prevent the Win7 installer from creating two partitions by default.
2) Reboot, using the Win7 install media.  Use the option to reformat the partition you created -- and continue with the Win7 install.  Reboot when you're done to confirm that Win7 will start OK.
3) Use the Win7 Backup option to create and burn a Win7 Repair CD.  You might need this later to repair the Win7 boot loader if the dual boot setup corrupts it.
4) Reboot, using the Ubuntu install media and install to the unformatted space on the drive.
5) When you reboot, it's probably going to go right into Ubuntu, so open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file to add an entry for Windows.
6) When you reboot now, you should see a GRUB menu with entries for Ubuntu and Windows.

You don't need enough RAM to run two OSs because you're only going to be running one OS at a time.

---

### Post by Impavidus on 2014-12-14
Install Win7 first. Make sure you leave enough unallocated disk space for Ubuntu. I think Windows needs at least about 40GB, Ubuntu runs comfortably in 20GB. With an NTFS data partition you can move files between Ubuntu and Windows. If you use legacy bios and MBR partitioning, make sure you don't get 4 primary partitions. If UEFI and GPT partitioning, read this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). Don't use wubi. Boot from a live disk and install Ubuntu alongside Windows. Use the automatic "install alongside" option for simplicity, or the "something else" option for maximum control.

---

### Post by sudodus on 2014-12-14
Please avoid "Install alongside", because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") it can remove Windows.

Select "***Something else***" at the partitioning window.

---

### Post by oldfred on 2014-12-14
The Something Else or manual partitioning install is a bit more complex.

Each of these shows all the screens and choices you get to install. You do not need to change the install of the boot loader from the drive that is sda, but all the other steps apply.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

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

If you just install Windows in BIOS mode without creating partition, it will use entire drive and two primary partitions. Then you should use Windows disk tools to shrink the main NTFS partition to make room for Ubuntu, and reboot immediately so it can run chkdsk. Do not create any partitions with Windows.

If a newer UEFI system, then you want Windows to create all its own partitions as several are required. The something else procedure is similar for Ubuntu.

---

### Post by John_Combe on 2014-12-15
In reply to Mark Phelps, you are saying to use a Ubuntu dvd disc in testing mode to run GParted to create two partitions before Windows 7 is installed in order to prevent Windows 7 from monopolizing the new hd? 
As a result of creating two unformatted partitions before hand the Windows 7 installation will create two partitions from the one I select during the install, (since you said Windows 7 would create two by itself); leaving the other unformatted partition (the 30 GB) alone for Ubuntu to use, correct?  Could I give the ubuntu partition more than 30 GB to use, as utility and useability programs would be be installed and space would be needed?
Could you break down step 4 as I am aware that when putting two operating systems on one hard drive, if one of them is Linux, that when selecting the installation partition that it would want to format it?  I do not want to erase the Windows 7 partition in the process of installing Ubuntu. I am aware that creating multiboot systems on one hard drive can be tricky.

Oldfred in response to your post, I find the Something Else option daunting; I am a Windows 7 user myself and I am aware Microsoft and Apple making things like installation easy has made using Linux operating systems look hard, but I know that while modern Linux distributions are much easier to use now than versions years ago, the installation process however makes people turn away.  If someone knows how to do it of course it can be simple, but people are used to not working at installing an operating system. I am old enough to remember that reinstalling windows 95, 98, and XP being a pain with having to swap driver discs all the time; while now Windows 7 and 8 have most drivers for hardware preinstalled, unless specialized hardware is installed then it gets annoying (gaming video cards, motorized cooling systems, etc).

---

### Post by Mark Phelps on 2014-12-15
> In reply to Mark Phelps, you are saying to use a Ubuntu dvd disc in testing mode to run GParted to create two partitions before Windows 7 is installed in order to prevent Windows 7 from monopolizing the new hd? 
No -- I said to create one partition, formatting it NTFS.  This prevents Win7 from creating two partitions -- which is what it does by default on an unformatted drive.

> As a result of creating two unformatted partitions before hand the Windows 7 installation will create two partitions from the one I select during the install,
No -- do not create any new partitions with Win7; instead, select the partition you created and have the Win7 installer reformat it as part of the installation.

>  leaving the other unformatted partition (the 30 GB) alone for Ubuntu to use, correct? 
No -- do not create a partition for Ubuntu in advance.  Create that when you boot from the Ubuntu installer, using the something else option.

> Could you break down step 4 
See oldfred's post #5 for details.

---

### Post by Impavidus on 2014-12-15
> **John_Combe said:**
> Could I give the ubuntu partition more than 30 GB to use, as utility and useability programs would be be installed and space would be needed?The 30GB limit is only applicable to wubi installs, and as those are obsolete that limit is not applicable at all. Programs don't take much disk space. User data often does, depending on what you do on your computer.

---


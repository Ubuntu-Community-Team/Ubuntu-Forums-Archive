---
title: "Ubuntu 14.04 LTS unable to find windows7/HDD. Can't install."
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by fred56 on 2015-06-14
First off Hello! Have used ubuntu in various forms for a few years now off and on. I decided to dual boot my old desktop pc with w7 and ubuntu 14.04 LTS. I've tried now for a week but I cannot get ubuntuo to find the C: drive. The pc was made in 2009 and I don't think the motherboard can handle UEFI- it's an Asus M3A78-T. AMD Phenom x940 cpu, and 2 HDD. I thought maybe I could change from MBR to GPT. Ubuntu can find the storage drive which is a 1.5TB Samsung, but I was unable to partition it in ubuntu installer to install onto it. The drives are both SATA. From reading on the forum here there is a way of checking with f disk and g disk to rule out a few things. I even installed 8.04 and thought I could just upgrade from there but to no avail! L
The last thing I've tried was installing from wubi.exe. All was going well untill it resets to boot up first time and I get  "No Root File System- Please correct this from the partitioning menu". Nice try! Anyhow, If anyone is able to give me a hand with this it would be greatly appreciated. I'm not a linux expert at all so go gently!!

Many thanks.

Fred

---

### Post by yancek on 2015-06-14
I don't think it is possible to upgrade from 8.04 and wubi is no longer supported.  Using the Ubuntu install DVD, select the Try Ubuntu icon on boot and when you get to the Desktop, open a terminal and enter this command:  sudo fdisk -l(Lower Case Letter L in the command) and post the output here.  The command will not change anything but simply output information on drives/partitions currently connected.  What happened when you tried to install to the external?

---

### Post by grahammechanical on 2015-06-14
You have got me confused.

If you cannot install 14.04, then how was it possible to install 8.04? I also, think that to use GPT we need a version of Ubuntu that comes with Grub 2 and I think that 8.04 has Grub legacy and not Grub 2.

We need to determine whether the system does have GPT which is usually part of UEFI, but not necessarily so. Or whether it has the 4 primary partition limitation that comes with a Master Boot Record (MBR)

Either way, it is my understanding that it is best to use Windows utilities to defrag the Windows disk and to do so more than once, making sure that Windows loads each time. And then to use Windows utilities to resize/move/delete Windows partitions to create unallocated/free space that the Ubuntu installer can use to create at least 2 Linux partitions from. One will be for Ubuntu the other for swap.

When you run the Ubuntu 14.04 live session load GParted and see if it sees the hard disks and the partitions. Take a screen shot and add it to this thread. Or run a Windows 7 utility that shows the disks and partitions and take a screen shot and post an image in this thread.

Regards.

---

### Post by fred56 on 2015-06-14
Thanks for the reply. I will post the outputs of fdisk-l soon. The fact I used to run 8.04 years ago made me think it would be straight forward to install 14.04. Here are shots of my Drive set up. F: is the USB with Ubuntu on. I'll follow your other steps first and post up results of fdisk-l. Thanks very much for the help.[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/DISK_1.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/DISK_1.png.html")[/IMG][IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/AOMEI.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/AOMEI.png.html")[/IMG]

---

### Post by fred56 on 2015-06-14
Ok, here are the shots from the live ubuntu. 

[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20151416.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20151416.png.html")[/IMG]

[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20151627.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20151627.png.html")[/IMG]

[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20151627.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20151627.png.html")[/IMG]

[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20151627.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20151627.png.html")[/IMG]

[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20151854.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20151854.png.html")[/IMG]

Regards

Fred

---

### Post by yancek on 2015-06-14
I'm not really sure what you think the problem is as the output you posted from fdisk and gparted clearly shows all three physical drives with partitions.  You have sda which shows as 465GB, sdb which shows as 1.5TB and sdc which is an 8GB drive including I expect, the Ubuntu Live/install media.  You won't be able to install Ubuntu to the 1.5TB because you have it formatted as ntfs which is a windows filesystem.  You would not be able to install windows on a partition with a Linux filesystem either.  The sda1 you show in your output is what windows users refer to as the C drive which is often used interchangeable to refer to an entire drive or a partition.  If you want to install to the 1.5TB, delete or resize the partition on it and create unallocated space on which to install Ubuntu.  You can do that from windows or the Ubuntu install media.  You can not create a Linux filesystem from a default windows install.

---

### Post by fred56 on 2015-06-14
I tried unallocating 100GB on sda1. When I'm on the install menu I'm unable to find the unallocated space. Only sdb shows up. Or is this because it's formatted NTFS? On my laptop I have windows 7/Ubuntu 14 installed to the c: drive. This is also NTFS.

---

### Post by fred56 on 2015-06-14
[IMG][[IMG]http://i67.photobucket.com/albums/h316/Farmer_Fred84/Screenshot%20from%202015-06-14%20180308.png[/IMG]]("http://s67.photobucket.com/user/Farmer_Fred84/media/Screenshot%20from%202015-06-14%20180308.png.html")[/IMG]
This is what I get at install with the unallocated space.

---

### Post by yancek on 2015-06-14
> On my laptop I have windows 7/Ubuntu 14 installed to the c: drive.

That is a wubi install.  WUBI= Windows UBuntu Installer.  This software was designed to install Ubuntu on a windows partition to test it in much the same manner in which you would test Ubuntu using a Live CD.  It was never meant to be used in the same manner as an actual install on a separate partition.  Wubi is no longer supported by the Ubuntu developers and will not be available in future releases.  

I'm not sure why you can see the unallocated space on the first drive (sda) on GParted and not from the installer of Ubuntu.  Do you select the manual installation method, called "Something Else" in Ubuntu?

---

### Post by fred56 on 2015-06-15
I installed on my laptop by bootable USB. I then just allocated partition in the installer and away it went. 
This is the tricky thing, not being able to find sda in the installer. I tried a wubi install and that fails too as can't find drive.

---

### Post by oldfred on 2015-06-15
Please attach screen shots, not post in line. You can use advanced editor and use paperclip icon to attach. And do not post terminal or test as screen shot, just copy & paste. If longer then use code tags to preserve formatting and make easier to read. You use # to add code tags in Advanced editor.

Last supported version of wubi was 12.04.
 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Several similar sets of instructions on installing to a second drive with screen shots.

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

### Post by fred56 on 2015-06-15
Thanks Fred,

Apologies for not posting the screenshots correctly. I haven't installed with wubi, as that failed as well due to not finding a HD. Ideally I will have Ubuntu on a partition of c: drive next to windows. Will have a read through the links. I oculd just live with Hardy Heron!!

---

### Post by fred56 on 2015-06-16
Hi, just a thought- if I were to put a SSD in my pc and reinstall w7 onto that and then ubuntu, would I be having the same issue and not being able to detect w7?

---

### Post by fred56 on 2015-06-16
Hi, just a thought- if I were to put a SSD in my pc and reinstall w7 onto that and then ubuntu, would I be having the same issue and not being able to detect w7?

---

### Post by oldfred on 2015-06-16
SSD should be same, but there were issues with some current versions of Ubuntu (thru 14.04) not seeing Windows 8 and erasing entire drive. 
Best to partition in advance and only use Something Else to install.

You do have to make sure Windows is not hibernated (Windows 8 always is) and does not need chkdsk. Windows always needs a chkdsk after a resize to after you install Windows reboot into Windows and use it to resize it with its disk tools, then reboot again to run the chkdsk. Then use gparted on live installer to create partitions for Ubuntu and use Something Else on installer to install.

---


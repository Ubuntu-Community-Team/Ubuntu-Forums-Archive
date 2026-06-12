---
title: "Dual boot two Linux distros"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by Roger_Williams on 2016-09-21
I've loaded Ubuntu 16.04 on an older Dell laptop, Core2Duo, 4GB, 750GB hard drive. I'm new to Linux but have been using Windows and MacOS for over a decade. I am technical but a dummy when it comes to Linux. I tried running Kali in virtualbox but with only 4GB on the system that was pretty much useless. What I would like to do now is have a dual boot of Ubuntu and Kali. The drive is big enough so I would like to half it. Ubuntu is already installed and I have an encrypted home folder. I tried running the Kali installation and it fails when I get to the partitioning section because it can't find anything to use. I booted into Ubuntu and tried to use gparted to create a free partition for Kali but wasn't able to resize or do anything. I'm new to Linux and gparted so maybe there are some simple steps I'm missing? 

[IMG]http://i1383.photobucket.com/albums/ah318/rwilliams0926/image_zpsyq279dwg.png[/IMG]

---

### Post by oldfred on 2016-09-21
With full drive encryption, you then have LVM which is an advanced logical partition scheme. Also used to get around the very old MBR(msdos) limits of 4 primary partitions.
Gparted will only show the physical partitions /boot & the one the LVM is in. You have to use LVM tools to edit and add logical partitions.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Unless full drive encryption needed or desired, often better to use standard partitioning. And if not installing Windows you can use the newer gpt (used with UEFI) in BIOS boot mode if you add a bios_grub partition. Windows only boots in UEFI mode from gpt. 

Do not know if Kali can be installed in LVM? 
In Ubuntu you have to use Something Else to install into precreated LVM.
        
 [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Roger_Williams on 2016-09-21
> **oldfred said:**
> With full drive encryption, you then have LVM which is an advanced logical partition scheme. Also used to get around the very old MBR(msdos) limits of 4 primary partitions.
Gparted will only show the physical partitions /boot & the one the LVM is in. You have to use LVM tools to edit and add logical partitions.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Unless full drive encryption needed or desired, often better to use standard partitioning. And if not installing Windows you can use the newer gpt (used with UEFI) in BIOS boot mode if you add a bios_grub partition. Windows only boots in UEFI mode from gpt. 

Do not know if Kali can be installed in LVM? 
In Ubuntu you have to use Something Else to install into precreated LVM.
        
 [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Thanks for your reply so if I'm reading this correctly I'll have to reinstall Ubuntu from scratch and select the LVM option. As far as I remember when installing Kali it gives me the option to use LVM as well during the partitioning stage so would I just select that option?  Basically Ubuntu install first use LVM option during setup and partitioniing don't bother with the encryption it's not needed anyway. Then after Ubuntu is in run the Kali setup and select the LVM option during the partitioning stage. Does that sould good?

---

### Post by oldfred on 2016-09-21
In Ubuntu the LVM option erases entire drive. You should not have to reinstall Ubuntu unless you want to change from LVM to standard partitions, either MBR or gpt.

So if Kali is using the Ubuntu LVM logic you cannot dual boot with default LVM install option. 
Only using Something Else may it work.

---

### Post by Roger_Williams on 2016-09-21
OK, when I installed I never chose LVM. I just know/think during both installations it gives me the option. Is the issue Kali then? The installation is new and there is no data so I can easily blow it away and start over tonight. I just want to know the proper steps if there is any to get them dual booting. Forgive my ignorance but as I said I'm pretty new to this.

After doing a search I found this info. So it looks like maybe encrypting or my noob choices when I installed Ubuntu might be the issue? Just wondering if I reinstalled Ubuntu tonight if I could get this going?
 
[B]Method1: Preferable one if you have already installed Ubuntu in legacy mode then install the Linux in the same mode.
[B]Step1:Make a bootable live USB with kalilinux and follow the boot setup instructions to set boot priority #1 as live USB [https://craftedflash.com/info/ho...]("https://craftedflash.com/info/how-boot-computer-from-usb-flash-drive")
Or if you know how to setup boot priority no need of above reference.
[B]Step2:Here you can choose either try Kali live or graphical install.
[B]Step3:If you choose try Kali live and like to proceed for the installation press window+s on keyboard and in the search column type install select install option and follow the instructions properly.
[B]Step4:While partition the disk make sure that you have to make three partitions one for swap area, one for root and the other one for home.
Swap area:4gb space is enough
/(i.e root):Minimum 6gb and
/home.
[B]Step5: after the partition continue to the installation and grub is installed automatically check whether Ubuntu is is detected by the kalilinux grub. If in case not detected do boot repair with live USB in kalilinux to load grub menu
[B]Method2: if Ubuntu is in uefi mode then install kalilinux in legacy mode and follow the same procedure for the installation.\


[/B][/B][/B][/B][/B][/B][/B]

---

### Post by oldfred on 2016-09-21
Those instructions look fine for a standard MBR or gpt partitioned drive.
You can share swap as long as you do not hibernate. Do not share /home.
But often better to create a larger /mnt/data partition with just user data. Then that can be used in every install.

You choose the LVM option. What it does not say, but should is like first option in [COLOR=#ff0000]RED[/COLOR] that entire drive is erased. And LVM does not use the standard partition tools that most instructions refer to but advanced LVM tools are required.[ATTACH=CONFIG]271301[/ATTACH]

---

### Post by Roger_Williams on 2016-09-21
OK great I'm going to give it a shot tonight. I wont be sharing anything because the drive is big enough. I just meant in general if the instructions were correct. I will update tomorrow or tonight depending on how it goes lol.

---

### Post by Roger_Williams on 2016-09-22
OK last night was a lot of fun. After trying different things with no success. I tried installing Kali first and then Ubuntu which was the simplest procedure. Ubuntu saw the Kali installation and offered me the choice of installing alongside Kali. The only problem was once I resized the drive when it tried to apply the changes the Ubuntu installer said there were unresolved errors on the drive and wouldn't complete grrrrr

Is there a way to totally wipe the disk and just install from scratch? I tried a Kali installation with the choice of using the entire disk but still get the uresolved errors when I try to install Ubuntu.

nvm tried it on another disk with a fresh Kali iinstallation and got the same error. I'll figure something out.

---

### Post by Roger_Williams on 2016-09-23
It is done! The fact that it was a moderately new installation with no data made the whole process possible and easier. I used the Ubuntu live CD and gparted to wipe out the existing partitions. Then I created two 350GB partitions. Installed Kali first and pointed it at one of the 350GB partitions. Then installed Ubuntu but I didn't choose the install alongside Kali option which would have divided the 350GB partition Kali was on. I choose the something else option and pointed Ubuntu at the other 350GB partition. After the installation had both in GRUB and I was all done for the night. :)

---

### Post by oldfred on 2016-09-23
Glad it worked, you can change to solved.

You may note that you are not using much of either partition.
df -h

And your data will be what grows the most. I have multiple Ubuntu installs and use 25GB for each, but have a large /mnt/data partition that I use in all of them.

---

### Post by Roger_Williams on 2016-09-23
Thanks for reminding me to mark it solved. Yeah I'm just starting out now so my data is pretty much non-existent. I do have 10TB of external storage and tend to keep very little on my computers.

---


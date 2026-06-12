---
title: "&quot;This computer currently has no detected operating systems&quot;"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by pmygarcia on 2014-08-24
Hi everyone. Not only having trouble, but also new to linux/ubuntu, so i don´t know if this should be posted here or in the "new to ubuntu" subforum, but i´m sure you´ll let me know if it´s the case.

I´ve built a new PC from scratch. I wanted dual boot with windows 7 and ubuntu, so i´ve read in some official ubuntu page i should install windows first, so i did. Then made a usb-thumb-drive-ubunto-boot-disk and tried to install, but was surprised by the fact it didn´t detected my windows OS ("This computer currently has no detected operating systems"). I´ve installed it on a brand new drive and have used windows 7 (64bits) installer to partition the drive in 4 partitions: first, windows madatory 100mb-I-don´t-know-for-what-purpose, second, where i intended to install ubuntu later, third, where i actually installed windows 7 64 bits, and fourth, some storage space. Every thing got formated in NTFS. I also have other fisical drives for additional storage space, but i will focus on this drive which partitions i´ve just described.

I´ve just read some topics related to this message, but no one seemed just like my case. It seems some "fixpart" software may be the solution, but i´m a little suspicious about it, specially because i´m new to linux/ubuntu. But i´ve even tried downloading it but it gave me some erros upon trying to install on ubuntu live and in windows readme instructions called for a "gdisk" command where the "fixpart" package didn´t come with such executable, only fixpart it self.

So i began to fear a little what should have been easy and decided it was time to register and ask for help first... So... please, help!

OBS: oh, just forgot to say, apparently windows 7 is booting in BIOS mode and i´ve tried to run ubuntu installer in UEFI mode, by setting bios options and by explicit boot option when pressing f12 on boot.

OBS2: and just to clarify, although i recive the "This computer currently has no detected operating systems" message, when i go for the manual partitioning option, it shows all my 4 partitions correctly (apparently).

---

### Post by oldfred on 2014-08-24
If you installed Windows in BIOS mode you have MBR(msdos) partitioning with its 4 primary partition limit.
The fixparts issue is where you had Windows 8 (or occassionly 7) installed in UEFI mode and reinstall Windows in BIOS mode. Windows only boots in UEFI mode from gpt drives and when reinstalled in BIOS mode incorrectly converts drive to MBR leaving the backup gpt table. Linux then sees both MBR & gpt and fails.

You have the 4 primary partition limit issue. And Linux cannot install to NTFS partitions. So if that is a empty partition just delete it and then you have one available primary partition to be the extended partition. And in the extended partition you can have virtually an unlimited number of logical partition.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

How you boot installer is how it installs, so be sure to always boot in BIOS/CSM/Legacy boot mode. Do not turn on UEFI mode.
      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If building your own PC often better to have two hard drives or an SSD & a hard drive. Then you can install each system in a different drive and avoid a lot of issues.

Windows 7 can be installed in UEFI mode, but you have to convert to flash drive and do some updates. And then drive has to be gpt partitioned.

---

### Post by pmygarcia on 2014-08-24
Ok, thanks oldfred, now i see it was a good idea to post my doubts...

I have some reading to do now, but there is something that´s not clear to me already: apparently no topics/observations made by oldfred lead to ubunto not recognizing my windows OS. How should I expect it to do so?

EDIT: ok, i just deleted the partition I previously created for Ubuntu (was empty) and left the space unallocated. Booted and pressed f12 to invoke bios boot menu and chose the usb drive in the non UEFI option. And then it detected windows. But then there is another question: "Install alongside" option will install in same partition and mess with things? Because the procedure to use "something else" option involves various partitions I'm not familiar with, and there is the primary/logical thing i still have to figure out... In other words, I'm hoping the "install alongside" is the right one for me and it will create the right partitions in the unallocated space and install ubunto there. Am I right?

---

### Post by oldfred on 2014-08-24
Did you just delete the NTFS partition or reformat it to ext4? If it is unallocated space and that is the size you want for both Ubuntu's / (root) and swap then along side should work. But if too small, it may auto shrink Windows.
While that usually works, I still prefer manual install. If you have a fair amount of RAM it will make a very large swap which generally you do not need.

I know it is more work to manually install, but if you follow these instructions it should work.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

While you cannot do it during install, I prefer smaller system partition for both Windows and Ubuntu. Then either larger /home or data partitions. And dual booting with Windows a larger NTFS shared data partition is worthwhile. You can just leave room or partition in advance with gparted. Or use gparted if you left room during install.
If you want the separte /home you have to use Something Else as all auto installs just create / & swap with some size algorithm on space for / & swap. I prefer to specify sizes as shown in the something else examples.

---


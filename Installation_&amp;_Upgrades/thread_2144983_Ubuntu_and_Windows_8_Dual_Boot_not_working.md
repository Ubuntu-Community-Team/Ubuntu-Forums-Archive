---
title: "Ubuntu and Windows 8 Dual Boot not working"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by Gurinder25 on 2013-05-14
Hi there everyone, 

    My name is Gurinder Hans and this is my first post here. Recently I got into ssh, git and all this server stuff. So I decided to install Ubuntu 12.04 LTS because through the terminal you can run all these cool commands. So what I did was create a partition about 40gb and installed Ubuntu on it manually. I have also tried selecting the option 'Install Ubuntu alongside Windows 8 '. Also please note that I fresh installed Windows 8 too and my pc didn't come with Windows 8 pre installed. I have upgraded from Windows 7 which came pre installed with my pc. I have tried installing ubuntu and Windows 8 around 3 times (fresh install). The problem is that each time after I take out the installation usb and restart my computer my pc hangs on the oem screen for a while. It is ridiculously long and after when it gets to the ubuntu boot loader and I boot into ubuntu I have to use the keyboard to login and move around because the mouse doesn't get detected for around 5 mins. Everything else seems fine. Now on the windows side when I boot into windows and login I get an error saying unknown device found and it didn't give me any specific error but if you guys out there can help me find the solution to this it'd be really great because I love Ubuntu and want to run it along Windows 8 which I really like too :) Thanks. Also I have attached the windows 8 error that I get and hopefully it helps.

---

### Post by oldfred on 2013-05-14
I do not know Windows 8 errors, that may be for a Windows forum.
Is your system UEFI or BIOS. A few Windows 7 systems were UEFI, but most are BIOS with the 4 primary MBR partition limit. Did you install Windows 8 into another primary partition?

Best to see details.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by Gurinder25 on 2013-05-14
Hey oldfed, So in order to do this, Should I install Ubuntu again? Also my system is BIOS and when I installed Windows 8 it was a clean installation by deleting all volumes and having one allocated space and then I let windows take care to create its primary and system reserved partition. After Windows 8 was installed then I installed Ubuntu 12.04 LTS. Right now I have done another fresh install of pc and only have Windows 8 running at the moment. I guess I could install Ubuntu one last time if needed.

---

### Post by oldfred on 2013-05-14
Often minor issues then that Boot-Repair can fix. Best to see what issues are and only then if issues not easily resolved a new install may be a good alternative since you have nothing to save.

Run the Boot-Info report to see what is where.

---

### Post by Gurinder25 on 2013-05-14
So install UBUNTU?? or i can do this from Windows 8??? Also do you recommend a specific software to create a partition for Ubuntu because when i create one with windows built it disk manager i get an error while formatting the parititon.

Thanks,

Gurinder Hans

---

### Post by oldfred on 2013-05-14
I thought you already had partitions. Or were you installing wubi inside Windows? 

NO never create partitions with Windows, but do use Windows disk tools to shrink Windows NTFS partition and reboot so it can run chkdsk and make repairs for its new size.
Have you used all 4 primary partitions? I hope you did not create partitions with Windows as it converts to dynamic which does not work with Linux.

Post this then from liveCd.
sudo fdisk -lu

---

### Post by Gurinder25 on 2013-05-14
hey,

    At the moment i only have Windows 8 installed and as usual windows creates two partitions one for OS and one for backup and boot repair so i only have two partitions.
How would you recommend creating a partition, because I think the whole problem is that the pc cant detect the other partition for ubuntu and when I had ubuntu installed and booted into windows 8 and went to my computer i couldn't see ubuntu's partition. Also i have creating no partition from windows or shrinking space and have let ubuntu installer take care of paritions by choosing option on installer "Install ubuntu alongside windows 8".

Thanks,

Gurinder Hans

---

### Post by oldfred on 2013-05-14
Part of the issue is that Windows 8 is hibernated all the time so you think it boots faster. The LInux NTFS driver will not let you work with Hibernated or NTFS needing chkdsk to prevent damage.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
[http://www.eightforums.com/](http://www.eightforums.com/)

I prefer to partition in advance, but I want extra partitions. My standard suggestion.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Gurinder25 on 2013-05-14
Hey, 

    So this is what I should do. 
1) Shrink about 50gb of space
2) Start ubuntu installer
3) Create three partitions 
     i) One partition for Linux OS to location '/' about 7gb 
     ii) Create another partition for files location '/home' about 30gb 
     iii) Create last partition as swap area and give it rest of the space 

For partition 1 and 2 make them as primary and make third partition as logical? 

Finally start the installation process? 

Thanks, 

Gurinder Hans

---

### Post by oldfred on 2013-05-14
You can make them all logical. I would make / (root) at least 10GB perhaps more if you have space. Swap only needs 2GB as I do not recommend hibernation.
Or for 50GB 2GB swap, 15GB / and the rest /home. But if dual booting with Windows you really need another NTFS shared data partition, but then Windows does not need as much room.

Sizes are not critical. My own optimal partitioning is not so good a year or two later as I find I change how I am using system and different uses need some partition changes. Usually by then I decide to get a new large drive.

---

### Post by Gurinder25 on 2013-05-14
.

---

### Post by Gurinder25 on 2013-05-14
So make them all Logical -> Done
What about all there file systems make them -> NTFS even '/' root dir. Can you please list them out?
Thanks,
Gurinder Hans

---

### Post by oldfred on 2013-05-14
You have to use Linux format for Linux systems. NTFS does not support Linux ownership & permissions.
And Windows does not even let you create Linux file systems.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
Examples of installs, versions are not critical as process is the same, and screens have only minor changes, mostly graphics not functions.
 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

      
 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Gurinder25 on 2013-05-14
I installed Ubuntu 12.04 LTS by creating three partitions but I still get the same problem. I download the boot repair and tried to make Windows 8  boot by default but now I see 2 windows 8 options in boot manager on dev sda1 and dev sda2

---

### Post by oldfred on 2013-05-15
Boot repair copies the boot files from the 100MB hidden boot/repair partition to the main partition as a backup. But then grub finds both sets of boot files & will let you boot from either.

What problem?

If black screen have you added nomodeset to linux line in grub?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Gurinder25 on 2013-05-15
Hey oldfred,

     Thanks for all your help and staying along with me. I found the problem to this whole mess. It was my webcam which for some reason wasnt getting detected properly. As I took it out the windows unknown device error went away and when i restarted the computer it was fast as ususal and ubuntu detected mouse right away. Still I have to find a way to solve this mystery but i guess that isnt part of Ubuntu forums anymore. Anyways thanks for all your help.

Thanks,

Gurinder Hans

---

### Post by oldfred on 2013-05-15
Glad you got system working. :)

I have seen one or two threads on web cam issues. You can search forum or post new thread with your exact model and they will ask for some info from lsusb after you plug it in. I do not have webcam so do not know details. It may be some models do not work?

---

### Post by Gurinder25 on 2013-05-15
Hi,

One last question how would i mark this thread as solved??

Thanks,

Gurinder Hans

---

### Post by oldfred on 2013-05-15
See my signature. We have to have a temporary work around as forum was recently updated and do not have the plug-in for solved working yet. You have to edit first post which normally is closed after a day or so.

Also:
       Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


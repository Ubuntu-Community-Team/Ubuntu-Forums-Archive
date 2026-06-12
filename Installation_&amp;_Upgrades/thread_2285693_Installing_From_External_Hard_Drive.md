---
title: "Installing From External Hard Drive"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by Williamreed on 2015-07-07
Hi 

I am having issue with installing Ubuntu onto my Windows 8 machine. I have installed it onto my external hard drive. 

I have then shrunk my windows volume to allow it run dual operating systems 

but when I boot from the external harddrive i get this error 

peter anvin et al could not find volume info attribute

can someone please advise what i should do next 

Thanks

---

### Post by sinep2 on 2015-07-07
Do you mean you burned the Ubuntu ISO to the external drive, or do you have the OS installed on the drive, or did you just drop the ISO in the external drive?

---

### Post by yancek on 2015-07-07
> peter anvin et al could not find volume info attribute


Peter Anvin is the primary developer of the Syslinux bootloader among other software.  An interview with him at the link below.  You will see that message anytime you are booting a Linux CD/DVD/flash drive using Syslinux.  It is a simple matter to boot an Ubuntu iso file from a hard drive using the Grub2 bootloader but you don't explain how you are trying to boot and don't seem to have a system with Grub2 installed?   I am also confused about exactly what you have done and how you are trying to boot so answering the questions posed above would be a good starting point.

[https://www.linux.com/news/special-feature/linux-developers/654773-30-linux-kernel-developers-in-30-weeks-h-peter-anvin](https://www.linux.com/news/special-feature/linux-developers/654773-30-linux-kernel-developers-in-30-weeks-h-peter-anvin)

---

### Post by Williamreed on 2015-07-08
Hi I think i have made some progress. let me give you some more info. 

I have managed to instal Ubuntu onto my external hard drive (i think). i then reboot my pc (Shift + restart) I am then able to request that i boot to another operating system. I choose Ubuntu. 

I get this error message. 

Windows failed to start. a recent harware or software change might be the cause to fix the problem:
1 insert your windows installation disk and restart your computer
2 choose your language settings 
3 click repair your computer 

File: \ubuntu\winboot\wubildr.mbr 
status: 0xc0000225
Info : the application or operating system counldnt be loaded because a required file is missing or contained errors 

I am then able to choose to boot with windows 8.1 which works fine. 

Can anyone tell me what i have done wrong. 

Thanks

---

### Post by ubfan1 on 2015-07-08
Did you read the first thread (sticky) in this forum ?
[h=3][Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")[/h]You have a separate disk, you made room on your internal disk, use one of those places to install Ubuntu.  There are wubi instructions around, but it is no longer an easy way just to try Ubuntu.

---

### Post by oldfred on 2015-07-09
If you have Windows 8 pre-installed, you need to partition external drive with gpt partitions and have an efi partition. I suggest a smaller / (root) partition and use rest of drive as shared data or NTFS partition(s). You can have /home separate or configure all your data normally stored in /home like Documents, Music, etc is really on shared data partition(s).

But install to external must be UEFI with ubuntu boot loader on external drive. Default install will not correctly configure it, as ubuntu only installs its boot loader to sda. That will let you dual boot, but drive will only be bootable from your system. Best to copy ubuntu folder from sda's efi to sdb.

Most install instructions are for dual booting on one drive, you can skip the shrink Windows instructions. But you still should backup Windows & efi partitions. You should have those backups even if not installing Ubuntu.
       UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html
[/URL]
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[       ]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
    [URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]
[/URL]

---


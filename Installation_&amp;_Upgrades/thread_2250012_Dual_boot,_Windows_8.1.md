---
title: "Dual boot, Windows 8.1"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Deepesh_Thapa on 2014-10-26
Dear all, 

I am using an EFI modeled motherboard running windows 8.1. I have asus motherboard which is kinda new technology compared to old BIOS legacy system. I got fed up of windows and want to try linux. So as said in the installation guide i used live usb and boot with it. I made a simple 50 gig partition to the c: and now it has seperate disk partition. OK, i ran the installation through USB booting by turning off the Fast boot and enabling the CSF or something like that in the BIOS setting. The installation/bootable usb runs well and i went to install linux. During installation i chose install alongside windows. I did not chose to install using partitions so i suppose it got installed with windows. The installation was a success and restarted the laptop. However, now i cannot dual boot nor I can use linux installed on my device nor I can uninstall it nor i can find where it is installed, and infact i cant do anything beside running windows ohh yea windows runs properly. I am not to much techy guy but wanna give linux a go and need to learn. So could anyone suggest or direct me to this problem.

One more thing, the forum says try boot manager or things like that and again says it wont work with windows 8 or EFI system. what can i do I really need this OS

ubuntu 14.10

---

### Post by Bucky Ball on 2014-10-26
Welcome. You want Boot Repair, not boot manager:

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

If you want to make sure you have it installed Ubuntu on its own partition, boot from the LiveUSB>Try Ubuntu>when at the desktop launch Gparted and look for the mount points / (EXT4 partition) and /swap.

---

### Post by ajgreeny on 2014-10-26
Windows is undoubtedly running in UEFI mode, so ubuntu must also run in UEFI mode in order to avoid having to go into the UEFI/BIOS each time you boot in order to set it correctly for each of the two OSs..

I think, but I'm not sure, that Boot-Repair in my signature can change the current ubuntu install from CSM to UEFI so have a look at that to find out if I'm correct.  It will also help anyone else who appears trying to help you out with this problem.

If not you will need to reinstall ubuntu, making sure this time that you choose to boot the DVD/USB in UEFI mode and also choose "Something Else" in the disk preparation stage, or you could find your Win 8.1 has been overwritten.

For general info on UEFI have a good read through [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by Bucky Ball on 2014-10-26
> **ajgreeny said:**
> ... Boot-Repair in my signature can change the current ubuntu install from CSM to UEFI ... 

What I've been led to believe by those in the know ...

---

### Post by Dennis N on 2014-10-26
For newer ASUS boards, in boot menu leave CSM Enabled and set secure boot OS type to "Windows UEFI mode". When booting the installer media from the boot menu in the UEFI-bios, there will be two entries in the boot menu - the one to use has UEFI as part of the description (something like "UEFI Kingston Data Traveler..."). If correctly selected, it will boot to the black background screen on this page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). From there use the first selection for live session. From there you can try and then install to HDD.

---

### Post by Deepesh_Thapa on 2014-10-26
i have already installed ubunt in two ways, one by alongside windows and other by partition. My c: contains windows, and I partition the d drive and followed the same steps as told in the website to configure he partitions like /home and other stuffs. Now what I get is i cant access d: from windows its hidden but when I check disk management it says Healthy(Primary partition) on three places and Healhy (recovery) . But I cannot still load UBUNTU . i keep on loading windows. i did the bootrepair and it says you are still running on UEFI system. I really dont know whats going on could anybody explain me how to boot ubuntu ones its been installed. the instalation guide says dont use boot repair for ubuntu 14.10, how do I run ubuntu without uninstalling windows. I dont understand why is it so much complicated. By the way I have tried disabling and enabling CSM, secure boot everything that could come accross but no luck. 

my device is asus N56V and got toshiba Harddrive,

---

### Post by Vladlenin5000 on 2014-10-26
You have two distinct issues but I'll solely address the 'confusion' about partitions: Any space used by Linux partitions won't be visible/readable from Windows, period. You no longer have "D:" if you used that space for the installation. First of all that's a Windows terminology not applicable anywhere else outside the 'Windows ecosystem' and secondly, Linux systems cannot be installed in NTFS partitions anyway. The default now is the EXT4 file system - again, not readable in Windows.
In a nutshell, this issue isn't an issue. It's exactly how things should be.

Regarding the boot problem, please read again and understand post #5.

---

### Post by oldfred on 2014-10-26
I do not know who added the note the Boot-Repair does not work with UEFI. 
It actually fixed UEFI boot issues when grub2 would not boot UEFI systems.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It has not been updated since Saucy but still works. It really just runs standard scripts to update your system. And almost all those scripts are still the same. 

But it will not make any changes unless you specify. 
And Boot-Repair's summary report is very useful for us to know your exact configuration.

---

### Post by Deepesh_Thapa on 2014-10-26
I have already installed ubuntu and it has taken space on the hard drive . I cant load it , it just goes back to windows everytime I reboot my system. i did the normal partition and did exactly what it said on the instalation guide about installing ubuntu using own partition. 









Now how do i run this OS, ok just dont worry about windows, i hate windows anyways so how do I boot into UBUNTU

---

### Post by Vladlenin5000 on 2014-10-26
I hope you followed this installation guide - [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) - because it's the only one pertinent to your situation.
That say I strongly recommend you read again posts #5 and #8.

---

### Post by Deepesh_Thapa on 2014-10-26
This was just a simple issue, i sorted it out. Well, basically everything was fine the instalation, partition but I missed a basic approach which was to comvert the USB flash drive into FAT32(default) format. Doing so will enable the live USB to install the UBUNTU into EFI mode which was lacking when I made an image file on NFTS formated flash drive. Thanks for your help ... it really opened my mind on how technology are changing...

---

### Post by Bucky Ball on 2014-10-26
Good news and easy oversight for a beginner. Didn't think of it here! Yes, must be FAT32 and MUST be completely blank. Best to format the USB fresh before commencing with the USB installer you use. Works for me. 

Good luck and please mark the thread as solved by following the second link in my signature. Post a new thread for any further issues/comments. ;)

---


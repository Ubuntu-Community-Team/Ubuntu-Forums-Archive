---
title: "Ubuntu install on P50 failed"
date: 2018-04-12
forum: Installation &amp; Upgrades
---

### Post by isagarran2 on 2018-04-12
Hello
I was previously on another laptop on Ubuntu 14.04 and I was very happy to be on Linux.

I got a new computer , a Lenovo P50 with Windows 10 installed. I is supposed to support Linux also. Perhpas not all functionnality but I don't care. If Ubuntu runs on it , it is sufficient.

My problem is quite basic. I put the DVD to boot and install Ubuntu 16.04. I choosed install gnome option. At the end, I am in a live session user without Ubuntu installed.

Could you give me some advices ? What did I do wrongly ?

I set in the bios Secure boot to disabled. I let UEFI only set as if i set another option, I'm no longer prompt with the option "install gnome"

Thanks for your help. I'll appreciate.

Regards.Isagaran

---

### Post by yancek on 2018-04-12
I would suggest you start with the official Ubuntu documentation at the link below on dual booting Ubuntu with windows 10 UEFI.  Almost any pre-installed windows 10 will be UEFI so you need to boot and install Ubuntu UEFI also and you need to also make sure that hibernation is totally off on windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mörgæs on 2018-04-13
In addition to the advice above I suggest that you try the soon to be released 18.04 in stead of 16.04.

---

### Post by isagarran2 on 2018-04-13
Hello,
Thanks for the advices. Alas, I've no choice on the version. My company certified 16.04 and not yet 18.04. I'l have a look on above link. It sounds good.
I'll let you know.
Regards.

---

### Post by isagarran2 on 2018-04-13
Hello 
I think I missed something. I follow the link advices

> 
Use a 64bit disk of Ubuntu.                                                                                          OK
Secure Boot                                                                                      "Off".                  OK
In your firmware, disable QuickBoot/FastBoot , set from "Quick" to     "Diagnostics"    OK
disable Intel Smart Response Technology (SRT).                                 No SRT Option   OK
You might want to use an EFI-only image to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.                                                                                       Not sure to understand. I have only a prebuilt DVD Ubuntu 16.04
Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI SecureBoot appeared in 12.10 and 12.04.2.              "16.04"         OK
Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "Identifying if the computer boots the HDD in UEFI mode" paragraph below)
                                                             UEFI/Legacy Boot set on     "UEFI Only"    OK
                                                             CSM support                         "Yes"                OK


Then I saved Bios and reboot first then I reboot on DVD
I got this panel 
[IMG]file:///home/jps/T%C3%A9l%C3%A9chargements/Photosandroid/New%20folder/DSC_0001.JPG[/IMG]
I choosed option 2 : Install Ubuntu Gnome
I didn't get usual panels for installation (for example, choose the disk, and so on)
I got this panel
[IMG]file:///home/jps/T%C3%A9l%C3%A9chargements/Photosandroid/New%20folder/DSC_0003.JPG[/IMG]
With 
"Ubuntu 16.04.1 LTS ubuntu-gnome tty1"
"Ubuntu-gnome login"

So for me it confirms me that I'm in UEFI mode installation

then the desktop appears. But I'm always in a session live. Ubuntu is not installed at all !!!
[IMG]file:///home/jps/T%C3%A9l%C3%A9chargements/Photosandroid/New%20folder/DSC_0005.JPG[/IMG]

I used sudo gparted
/dev/sda1     EFI system partition                    Fat32                      system               260MB                        boot, hiden, esp
/dev/sda2     Microsoft reserver partition          unknown                                          16MB                          msftres
/dev/sda3     basic data partition                     ntfs                         Windows            73,26GB                      msftdata
/dev/sda5     MyLinuxpartition                         ext4                        MyLinux             402,44GB
/dev/sda4                                                      ntfs                         WinRE_DRV       1GB                             hidden,diag

So I always need help. If you have some ideas, let me know.

Regards.jps

---

### Post by dino99 on 2018-04-13
when the installer (ubiquity) will ask you, select 'something else' to set your own install path choice : /dev/sda5, set it ext4;
 via gparted  you might want a separate /swap partition (~10 Gb) and maybe also a /home partition for your data (not mixing with ntfs ones.

---

### Post by isagarran2 on 2018-04-13
Hello,
Thanks for the answer. the problem is that i'm not requested to Install Ubuntu somewhere. No question at all.
desktop comes up without any question. I'm in the live session neither in the process installation.
regards.Isagarran

---

### Post by isagarran2 on 2018-04-14
Hello
 I've some news after multiple try, I viewed that my installation failed on "creating user".
So I changed, user, password, partition format but always on "creating user"
Looking at the log, I saw issue described in [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1208832](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1208832)
Now, I've no idea on how I have to go further. If you have any idea

Thanks

---

### Post by isagarran2 on 2018-04-14
good url is [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1208832](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1208832)

---

### Post by isagarran2 on 2018-04-14
Hello,    
          Found on google similar issue on custom ISO. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1718317](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1718317)    
          Even if I set a ten digits passwords (mixed case, one digit number) it wasn't sufficient. I set eleven digits, mixed case, two numbers, two special characters and installation completed    
          Thanks for your support.    
Isagarran

---


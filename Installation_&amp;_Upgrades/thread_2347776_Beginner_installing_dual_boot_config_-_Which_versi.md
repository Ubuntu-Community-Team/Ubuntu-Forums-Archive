---
title: "Beginner installing dual boot config - Which version: 14.x or 16.x?"
date: 2016-12-28
forum: Installation &amp; Upgrades
---

### Post by mtlian on 2016-12-28
Hello,

I have been reading many of the pre-existing post on this forum and much of it is over my head and is a bit too complex for me so I hope someone can answer my layman questions. I'm currently setting up a Dell Precision 5510 core i7 16GB RAM with a PCie SSD to dual boot in Windows 10 and Ubuntu. I am interested in installing the latest stable version but when I was browsing ubuntu.org's hardware section, I noticed that the DELL precision 5510 was not listed in the supported hardware for Ubuntu v16.x but was listed for 14.x . Does that mean that I should aim to install a 14.x version on my computer?

I've already installed Ubuntu 16.x but I've since deleted the install because I was having problems booting back into Windows and Linux, it required me to make changes in the BIOS every time. I ran into the problem that the ubuntu installer didn't find my SSD and followed some advice on DELL's website and got it to work, but it caused problems with the Windows boot manager and I believe that I did not have any writing privileges in Ubuntu as I couldn't transfer any files from Linux to a USB key (FAT32) or a external HD.

I believe my woes were caused by the fact that I didn't disable fast boot and certain other BIOS changes that are outlined in the following DELL support article:

[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

I would like to attempt installing Ubuntu again but I'm afraid of messing things up, **specifically on the last step of the Linux install. **

Here's an outline of my procedure (I'm not backing up because I have very little data on my PC and am not afraid to do a system restore if all hell breaks loose):

1 - Shrink my main partition (on my PCie SSD) in Windows to make room for Linux and a swap partition
2 - make a bootable USB drive and boot to it
3 - tweek the BIOS as per the article so that the installer will find the SSD  
4 - create a swap partition and configure the main installation partition
here is where I am uncertain. I got this procedure from a YouTube tutorial but I don't want to muck up my the Windows Boot Manager: [B]

5 - Under "Device for boot loader installation", should I select the partition from the list with Windows Boot Manager written in the right hand column?

[/B]Thanks in advance for answers to my queries; I'd like to have this second attempt at installing Ubuntu be the right one that will allow meet to easily boot between the recommended version of Ubuntu for my system and Windows 10.

---

### Post by oldfred on 2016-12-28
Still good idea to have a backup.
My Dell SFF system wanted a Windows backup, a Dell backup & I made a full backup with Macrium.

Some users have by mistake select an erase entire drive, thinking drive used the Windows definition of a partition, but erased the recovery partition also.

Are you installing to the same drive as Windows? 
Then use Windows to shrink the NTFS partition, and reboot immediately to allow it to run chkdsk. Do not create partitions with Windows. 
If you just want simple configuration of / (root) and swap you can use installer and auto install side by side, but must have Windows fast start up or always on hibernation off for the installer to see the Windows install.
If you want a more complex configuration like separate /home or data partition(s) usually easier to partition in advance with gparted & use Something Else to install and choose existing partitions.

Whether installing with BIOS boot or UEFI boot you always choose a drive like sda, not a partition like sda1. But with UEFI, grub will auto install only to an ESP - efi system partition on drive seen as sda. When you choose a drive with UEFI, grub knows that all boot files & folders go into the ESP.

More details in link in my signature. Best to at least review.
Couple of good links (also recommended in my link below).
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by mtlian on 2016-12-28
Thank you for replying. I didn't understand most of what you just said. Here are my main questions:

1 - Should I install Ubuntu v. 16.x or 14.x ?
2 - I am doing a slightly more complex install. I would like to keep windows hibernation ON if possible but I realize I must turn off fast boot. I am using the windows disk manager to shrink my NTFS partition and then choosing the "something else" option in the Linux installer to create a swap drive partition. My question was: **is my last step correct? Should I choose the partition with Windows Boot Manager on it as a location for "Device Boot Loader Installation".**

---

### Post by oldfred on 2016-12-28
Dell often needs newer drivers. It releases Sputnik which has drivers for its very newest systems.
But I did see that first sputnik released about when 12.04 came out was included in 14.04. Dell is one of the few vendors that does work with Linux.

So I would think 16.04 with long term support would be better than 14.04.

       5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

You may erase Windows if you leave its fast start up on. The Linux NTFS driver does not see any NTFS partition if hibernated. 
If you want you can turn it back on after the install, but will not be able to share any data between Windows & Linux. Windows fast start up keeps all NTFS partitions mounted. I have one Windows 10 install and I normally have a shared NTFS data partition so from Linux I do not attempt to read or write into the Windows system partition. But even data partition becomes unusable whenever Windows updates turn fast start up back on.

You never choose a partition like sda3 fro Device for boot loader install. Only a drive like sda (or sdb, sdc etc). With UEFI grub will correctly install when you choose the sda drive. If you choose a NTFS partition for the grub2 boot loader you break Windows.

---

### Post by mtlian on 2016-12-28
"[COLOR=#000000]You never choose a partition like sda3 fro Device for boot loader install. Only a drive like sda (or sdb, sdc etc). With UEFI grub will correctly install when you choose the sda drive. If you choose a NTFS partition for the grub2 boot loader you break Windows."

[/COLOR]I apologize but I don't understand what that means. I'm following a YouTube tutorial explaining how to dual boot windows 10 and Ubuntu. The last steps requires a location to install the Boot Loader. I previously chose the partition which has Windows Boot Manager written beside it. Is this the right choice for the location YES or NO?

Thanks for your help. I just started using Linux mint 4 months ago and am installing Ubuntu because I prefer it (to Windows) so I don't yet have the knowledge to understand most of what you are talking about.

---

### Post by yancek on 2016-12-28
You are using windows 10 which is probablly using UEFI so I would suggest you read the official Ubuntu documentation page on doing this at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

If your windows is using UEFI, then booting and installing Ubuntu UEFI is necessary and it will install the Ubuntu boot files in a separate folder on the EFI partition where the windows UEFI files reside in a separate folder.   When you boot the Ubuntu install media you can check this out by opening a terminal and using the command:  sudo gparted
That will open the gparted partition manager and you should be able to see where all your partitions, including the EFI partition, are located.

---

### Post by mtlian on 2016-12-28
I read through the link and it uses a bunch of acronyms that I don't know what they mean. I think that if I just boot from my USB key with the ubuntu ISO it should already be installing in "UEFI". I might try and research the part that talks about using gparted but within the installer's "something else" menu, there already is a list of stuff which I imagine are all partitions.

I presume that by EFI partition, perhaps you mean the partition that is labeled Windows Boot Manager in the Linux installer "under something else" and that if I tell the installer to put the boot files in there, it will not overwrite the windows boot manager but rather install the necessary boot file (perhaps the GRUB?) along side the Windows boot manager? So I'll take the answer you gave me as: YES, the partition labeled Windows Boot manager is the right place to install the boot loader.

one last thing: when I go into (What i think is) the BIOS to determine the order in which my computer tries to boot in, I had three items. Windows Boot manager, my SSD and ubuntu. Which order should this be in?
[B]
please keep in mind that I am a beginner at Linux and have no background in computer programming. Please try to avoid using acronyms and very technical lingo as this is meaningless to me. Also please try and answer my questions rather than impart other useful information that a more advanced user could understand. I do really appreciate the attempt to help me though, thank you.

[/B]To summarize my questions are:

-install boot loader on partition labeled Windows Boot Manager in the "something else" menu of the Ubuntu installer? YES or NO?

-Which order of boot priority (Windows Boot Manager, SSD, Ubuntu)?

---

### Post by ubfan1 on 2016-12-28
Put "ubuntu" first in the priority list, then SSD, then Windows Bootmanager.  That way, ubuntu will boot grub, which will offer you the choice of booting either Ubuntu or Windows.
I cannot believe the "Device for bootlaoder installation:" dropdown offers you the choice of a partition, like sda1.  It should offer sda.  the device.  you will use partitions above to select mount points. The answer is NO, no partition will ever be the right choice.  That said, it probably doesn't matter what you type there, it will go to sda.

---

### Post by mtlian on 2016-12-28
Gee I wish I could post a screen shot but I can't because I'd have to be in the installation procedure to do it. This is turning out to be a nightmare. Maybe I should stay away from Linux because I'm not a programmer, I only know basic C++ (for engineering).

So if I understand correctly, I should have no choices under the dropdown menu other than my SSD and my USB stick since that is all I have on my laptop that could possibly boot from. I might try the install again, I can always blackout if I'm presented with more choices than the two mentioned under "Device for boot loader".

---

### Post by oldfred on 2016-12-28
This shows screenshot of the combo box on where to install grub2's boot loader.
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

You only choose sda, not a partition. It should also show the full name of the drive. Example just says ATA Hard drive.

---


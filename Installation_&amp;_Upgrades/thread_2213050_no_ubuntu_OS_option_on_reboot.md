---
title: "no ubuntu OS option on reboot"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by david_williams2 on 2014-03-24
I am not a programmer, so am only going to put so much effort into this.  I have windows xp, and would like to look at ubuntu.  So, I downloaded wubi.  When I reboot, Windows, and Restore System, are the only OS options.  It appears that ubuntu is on my C: drive, but cannot read the disk files, or access anything.  I may need more help than can be provided in this forum, but if anyone is willing to help, I'd appreciate it.  

I'm editing this to give more info..... have an hp desktop with AMD Athlon 64x2 Dual core processor 3800+, 1.99ghz, 896 mb RAM.  Trying to look at ubuntu 12.04.4

---

### Post by oldfred on 2014-03-24
Wubi is just a large file inside your NTFS partition. It really uses the Windows boot loader to boot. Your boot.ini should have an entry for Ubuntu when you boot Windows. The grub menu is just to be like a standard install but is only to boot Ubuntu.

In Nautilus file browser you see Windows c: data as  /host.

Windows XP expires in early April, so do not run it after that. And running wubi in Windows would not be recommended.

Also wubi is being discontinued and the last supported version is 12.04. Wubi does not work on any of the new UEFI systems with gpt partitioning which all new Windows require.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by david_williams2 on 2014-03-25
thank you for your response.
wow.  ok, didn't understand a single word you said.  sorry.  like i said, there is no "ubuntu" OS (is this the boot.ini you talked about?) option on reboot, only windows and restore system.  how do i make ubuntu work?
what's a "nautilus file browser"?  i know windows xp support expires in april.... that's why i'm trying to get ubuntu to work.  and, i know 12.0.4 is the last version of wubi.
again, how do i make ubuntu work?

---

### Post by oldfred on 2014-03-25
If you want to get rid of Windows soon, you should not be using wubi as it runs inside the Windows NTFS partition and requires Windows to boot. 

If wubi had installed correctly you would get a ubuntu boot option also.

Nautilus file browser is one of the standard Linux file browsers similar to the Windows file browser in function that is in standard Ubuntu. Different flavors of Ubuntu like Xubuntu or Lubuntu may use different file browsers. 

With 1GB of RAM and an older computer you may need Lubuntu not Ubuntu. Full Ubuntu now with Unity desktop needs newer systems with a decent video processor. Ubuntu runs on my 6 year old laptop but is very slow. I turn Unity off and install another desktop and it still works well.

       [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

 Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

      
 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

   [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---


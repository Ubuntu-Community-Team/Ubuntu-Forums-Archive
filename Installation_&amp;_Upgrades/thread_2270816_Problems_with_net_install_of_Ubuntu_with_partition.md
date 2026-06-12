---
title: "Problems with net install of Ubuntu with partitions and Win 7."
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by JohnNicks on 2015-03-25
Hi All,
I'm stuck installing Ubuntu 14.04 with the partition part of the install. I am downloading and using the net install since I can't burn DVDs, so I just downloaded the mini.iso and burned it to disc and restarted.
I am trying to install Ubuntu 14.04 along a Windows 7 Home Premium, and I have a 250GB hard drive and have done the partition part, but I get stuck and can't get it to work right. It's listed now on the computer as follows. 

[LIST]
[*](windows) #1 - Primary 78.8 GB - B -K Ntfs  /
[*](Ubuntu) #5 logical 170.3 GB k ext41 /
[*](swap) #6 logical 1.0GB k swap swap
[/LIST]
I don't know how to get it to work right with mounting and it's not letting me mount both #1 and #5 partitions as / . I marked #1 as Bootable and still can't get through and would appreciate any help on how to proceed and keep my Windows 7, and add Ubuntu side by side Thanks.
Also, I don't have the original Win 7 Home Premium restore disks of any kind, and any help would be appreciated. 
John Nicks

---

### Post by yancek on 2015-03-25
> it's not letting me mount both #1 and #5 partitions as / .

It won't and it can't and it should not.  Set sda5 as root with the forward slash symbol ( / ) as the Mount point for the installation of the system.  sda6 is swap so just set it as swap, for the filesystem type.  sda1 should already be set as bootable if it has windows on it.  I've never used a netinstall so I don't know what options you have.

---


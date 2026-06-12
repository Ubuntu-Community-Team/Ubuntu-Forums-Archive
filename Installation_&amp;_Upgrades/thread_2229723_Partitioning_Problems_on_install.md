---
title: "Partitioning Problems on install?"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by dan114 on 2014-06-14
Hey everyone, I thought I would say hello to the forums first before I get to the meat of my post here. To give some background I have been using Ubuntu for about 6 months now, and I really like it. However, I still consider myself a novice, and for good reason when things like this come up. 

Anyway, I purchased a refurbished lenovo y410p this week, planning to dual boot it between Windows Server 2008 r2 and Ubuntu 14.04. I wanted to install Server instead of keeping Windows 8.1 since I can't stand the Metro interface, and this laptop is designed for gaming (I have multiple games for Windows already). I know I can Windows to work, so that's not the issue. The issue is getting 14.04 to install. Now I have done quite a few linux installations at school for different distros I wanted to try and I have also installed some on friends' computers, et cetera. This time is the first time I have had any issues. 

I proceeded to delete all of the partitions that came on the main 1 TB hdd (It has a 24 GB ssd for Expresscache) and tried to install Ubuntu. It gave me an error that said[SIZE=1]:[/SIZE][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=3][COLOR=#212733]

[/COLOR][/SIZE][/FONT][IMG]http://i.stack.imgur.com/a02Jy.png[/IMG][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=3][COLOR=#212733]
[/COLOR][/SIZE][/FONT]
. I tried to skip it at first. That didn't work. Next I tried to make another partition for GRUB on the ssd in the laptop, but that didn't work either. It said that it could not install GRUB to that partition. After that I tried to install it on the same disk along with the rest of the Ubuntu installation, which didn't work either. I tried this both in Legacy boot mode and UEFI boot mode. It gives me the same issue either way. When I don't click "Choose something else" at the menu it installs Ubuntu to my ssd, which I want to keep for Expresscache if at all possible. How do I fix this?

Here is some information that may help:
The laptop came with Windows 8.1 x64
The laptop has a 1 TB hdd AND a 24 GB ssd

---

### Post by yancek on 2014-06-14
The message you posted means you are using UEFI and GPT partitioning.  You can google that while you are waiting for a response.  I've not used UEFI so don't really have any knowledge of it.

---

### Post by grahammechanical on 2014-06-14
I have never seen that message but then again I have the old MBR boot system but I have had Grub fail to install and the solution was to create at least 1MB of unallocated space at the front of the disk. I had to do this when I wanted to run Ubuntu on a B tree file system (BTFS).

See the heading: Creating an EFI partition in this guide

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

May be that is what you need. It is my guess that you deleted the EFI partition that was set up when Windows 8 was installed and which Ubuntu could have used.

Regards.

---


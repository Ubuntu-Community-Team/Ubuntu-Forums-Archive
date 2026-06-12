---
title: "Install windows 7 in Ubuntu? Dual boot"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by lunchbowx on 2010-03-10
Hello!

I am pretty new to Ubuntu. I've been using Windows 7 for a while but then I decided that I'd like to give Ubuntu a try as well. Installation went fine, until the grub menu didn't show up, I thought "What the hell, screw Window I need to reformat my hard drive" so I did that and installed Ubuntu instead.
Everything runs perfectly, but I need to use several windows programs such as Autodesks Maya, specificly.

So the question is, how do I install Windows 7 using Ubuntu? I've asked several of my friends and been searching around but haven't really found anything, and my friends said that they didn't know for sure. The thing I know is that I need to create a new partition to install Windows in. Otherwise I'm lost!

Thanks in advance (I guess :D)

---

### Post by Dayofswords on 2010-03-10
you have to make a new unformatted partition for windows(you know that so good, use gparted)

then install it as you would normally choosing that partition

you'll lose grub so you have to restore it with a livcecd(look elsewhere for that how, as I'm not sure exactly how)

---

### Post by OrangeCrate on 2010-03-10
> **Dual-Booting Windows and Ubuntu**

Rarely, a user may experience problems dual-booting Ubuntu and Windows. I**n general, a Windows OS should be installed first, because its bootloader is very particular. A Windows installation usually occupies the entire hard drive, so the partition needs to be shrunk, creating free space for the Ubuntu partition.** (You should clean up unnecessary files and defragment the drive before resizing.) See changing the Windows partition size...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Dayofswords on 2010-03-10
orange, that would work if he had windows already


he has ubuntu and wants windows, can be done

---

### Post by OrangeCrate on 2010-03-10
> **Dayofswords said:**
> orange, that would work if he had windows already


he has ubuntu and wants windows, can be done

If he has XP, sure.

Vista/Windows 7 is much different, and specific instructions relating to those two operating systems should be followed.

---

### Post by wilee-nilee on 2010-03-10
Here is a grub2 link for post W7 install, step 11 is what your looking for to get Ubuntu up and running and grub2 reloaded with both OS.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by Peter7K on 2010-03-11
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)
Contains a beautiful explanation.

---

### Post by presence1960 on 2010-03-11
> **OrangeCrate said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

You do not have to uninstall Ubuntu to install windows- that is the biggest lie in here. Boot the Ubuntu Live CD or a gparted Live CD and use gparted to shrink the ubuntu partition. You can then either create an NTFS partition or leave it as unallocated space.

Next boot the windows DVD and install to either the NTFS partition or the unallocated space. When the install is complete reboot to insure windows boots fine.

One more step to go: Windows overwrote the GRUB bootloader on MBR of your hard disk. You need to reinstall GRUB which is a 30 second process. if you don't know how to do so post back here when you are ready to reinstall GRUB.

**There is absolutely no reason to remove a perfectly good Linux install to install windows because as that link orangecrate gave you says "_In general_, a Windows OS should be installed first, because its bootloader is very particular." Note the words in general. Yes it is a wee bit easier (especially for newbies) to install windows first but by no means is a rule.**

Here is the link I say you need to read: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

P.S. orangecrate's link is by no means wrong. But the notion that one should install windows first is wrong. If you already have linux installed there is no need to remove linux to install windows. That is unnecessary work. Installing windows after linux only adds one step to the process- reinstalling GRUB which takes about 30 seconds to do. So orangecrate I don't want you to feel I am attacking you, but I am saying that the idea you put forth is not the best course in cases where linux is already installed.

---


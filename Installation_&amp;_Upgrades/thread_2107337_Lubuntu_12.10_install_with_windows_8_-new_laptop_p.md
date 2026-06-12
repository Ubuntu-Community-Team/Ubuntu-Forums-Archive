---
title: "Lubuntu 12.10 install with windows 8 -new laptop purchased"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by kero4 on 2013-01-21
Guys,
 
After my initial post and testing the laptop in the store, I purchased Toshiba L855-S5112 with the I3 processor. All hardware worked in the store so I was happy with that plus it has a normal touchpad, not one of those advanced ones, I forgot what they were called.
 
So, cleaned up windows in case I want to us it occasionally which will be rare at most.
 
Steps thus far - disabled secure boot, disabled fast boot.
 
#1 the only way I can get the laptop to boot into lubuntu (on flash drive) was to set the boot to CSM. If I leave the setting on UEFI, it does not even see the flash drive with the lubuntu install on it. If left on CSM and flash drive not installed, laptop does not boot into windows.
 
Now I tried to boot via UEFI menu into the USB flash drive and I got a pop up about not finding a boot device (can't remember the exact error that showed up) despite usb being set as the first boot device on startup. The usb flash drive works in CSM mode and on non UEFI systems.
 
Question: how do I rectify this???
 
#2 I assume I should shrink the windows partition using disk management option by right clicking on COMPUTER, manage, disk management. The partition I wills shrink is the NTFS partition.
 
#3 Llubuntu ***"does not support ***[***UEFI Secure Boot***]("http://en.wikipedia.org/wiki/UEFI_Secure_Boot")***, unlike ***[***Ubuntu 12.10***]("http://en.wikipedia.org/wiki/Ubuntu_12.10")***, which would have allowed it to run on hardware designed for ***[***Windows 8***]("http://en.wikipedia.org/wiki/Windows_8")***. This feature will likely be included in the next release of Lubuntu.[[73]]("http://en.wikipedia.org/wiki/Lubuntu#cite_note-Lubuntu1210relnotes-73") In the meantime Lubuntu can be run on UEFI secure boot hardware but turning off"***
 
Question: does this statement above affect #1 above, as I have already turned off secure boot.
 
#4 I thought I read somewhere that I should create the lubuntu flash drive in UEFI mode, is this done through using unetbootin in windows vs creating in lubuntu like I have already done?
 
#5 granted I get to the point where I can install lubuntu on the hard drive, where does the lubuntu boot loader go in terms of partitions.
 
I have the following:
 
2 recovery partitions, 1 EFI partition and the large NTFS partition.
 
Once I get these answered I think I should be able to get this all taken care of.
 
If I missed anything, please let me know.
 
Thanks for the help.

---

### Post by oldfred on 2013-01-21
Use Windows to shrink Windows, but not to create partitions. Not sure if Windows 8 will still try to convert to dynamic or not as with gpt partitioning there is no limit on partitions anymore.

I like having a shared NTFS data partition, so you never write into the Windows system partition. I like smaller system partitions with large data partition(s) or /home. But I use data partitions and keep /home inside my / (root) of 25GB.

I do not know Lubuntu, but you can get Ubuntu and then install the Lubuntu desktop. If you install full Ubuntu you may get some packages you do not need like Unity. Because Lubuntu is more for older systems with limited processors or RAM, I assume you only really want the lxde enviroment.

       The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
# example
sudo apt-get install ubuntu-desktop

        Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

    
 Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
All Desktops in one:
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)

---

### Post by kero4 on 2013-01-21
Hi,

Thanks for responding.

Most important is needing questions #1, #3 and #4 answered.

Based on your reply, you think the problems most likely lie with the fact that Lubuntu does not support UEFI at this point until next version, and that is causing my problems with #1 as I posted?

I have no problem installing ubuntu 64 bit then installing LXDE however, I am not sure what unity is as I never used UBUNTU on lubuntu, is unity something to be concerned about?

YES, I love the LXDE environment!!!!

I love lubuntu because its low resource and clean and simple to use. On a new machine, even booting off the flash drive it's crazy fast.

Help on #1 3 and 4 please :)

---

### Post by oldfred on 2013-01-21
CSM is another name for legacy or BIOS mode. And until lubuntu supports UEFI better I think you will have issues. And that may be why you cannot boot flash drive in USB as it may not have it. Only the 64 bit Ubuntu has the UEFI secure boot, not sure about other versions and no 32 bit versions have UEFI.

Unity is the new gui with all the options on the left. It has improved a lot, but I still use the fallback gui which is similar to the old gnome2.

Once you have any Ubuntu installed you can install the others. At the login screen you click on the little gear icon in the upper right and select which gui you want.

---

### Post by kero4 on 2013-01-21
So, already shrank the partition.

Downloaded ubuntu 64bit and will install, then install LXDE and should be fine until lubuntu support UEFI directly.

Will update the thread once done.

---

### Post by kero4 on 2013-01-21
So, installed ubuntu, ran the boot repair and all is working just fine.

I installed LXDE and did not like it compared to actual lubuntu so I removed it and tweaked ubuntu as best as I could and will use the laptop as such until lubuntu supports UEFI which should be soon.

Thank you for the help, how does this thread get changed to solved?

---

### Post by mysteriousdarren on 2013-01-22
Just install vanilla ubuntu and add the environment after and change things. My laptop doesn't support UEFI either. I tried several ways, but thats the only one that worked. Good luck!

---

### Post by kero4 on 2013-01-22
I did not that, I installed ubuntu and then installed LXDE but did not like that combo as LXDE installed over ubuntu is not the same as LUBUNTU.

I unistalled LXDE and left ubuntu and tweaked it a bit for the short term.

Once LUBUNTU supports UEFI, I will just install that and remove ubuntu all together.

---

### Post by kero4 on 2013-01-24
Update: I realized I installed LXDE instead of the lubuntu desktop. Installed the lubuntu desktop and am very happy now.

---


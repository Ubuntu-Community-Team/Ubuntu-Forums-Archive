---
title: "Dual-boot set up along w/ Windows 8"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by ron177 on 2014-06-08
[h=1]Dual-boot set up along w/ Windows 8[/h]               
[LIST]
[*]     [Ubuntu]("https://launchpad.net/ubuntu")
[*]     [Questions]("https://answers.launchpad.net/ubuntu")
[*]     Question #249944
[/LIST]
                                          Asked by         [Ron]("https://launchpad.net/%7Eronald17b95")         a moment ago                     
             
                                                       
                                            Dear all,
 I am trying to have a dual-boot setup on my brand new Toshiba which  came preinstalled with Windows 8. I have run the Ubuntu installer and  have come to the menu where it asks for "Installation Type." Previously  when I installed Ubuntu on other machines, the Ubuntu installer  recognized that there existed operating systems and as such it always  gave me the option of choosing to install Ubuntu along side with the  original OS (say a Windows or a Mac). In this case, though, the Ubuntu  installer tells me the following message:
 "This computer currently has no detected operating systems. What would you like to do?"
 And then there are four different options:
 1. Erase disk and install Ubuntu
2. Encrypt the new Ubuntu installation for security
3. Use LVM with the new Ubuntu installation
4. Something else (you can create or resize partitions yourself, or choose multiple partitions for Ubuntu.
 Now I have no idea what options #2 and 3 are really, and I know I do  not want #1. But I also do know that #4 is way too difficult for my  level of skills. So here I am asking for help.
 Please advise what I should do.
 R

---

### Post by kansasnoob on 2014-06-08
Do NOT trust the automated parts of the installer at this point:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

It's a mess!

---

### Post by ron177 on 2014-06-08
So what should I do? How should I install Ubuntu? Is there a safer and easier way?

---

### Post by oldfred on 2014-06-08
If at all familar with partitions the Something Else install option is not all that hard.

But with new UEFI systems, you must do several things in advance.
Use Windows own partition tools to shrink Windows to make room for Ubuntu and do not create any partitions with Windows. Immediately reboot so it can run chkdsk and update itself. 
Turn off fastboot or the always on hibernation. Usually better to turn off secure boot for now.
Make good backups of all of Windows and the efi partition.

Then use Something else. You really only need / (root) & swap. Install grub boot loader to sda.
Examples of Something else:
       Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

Lots more info in the links in my signature. First couple are vital. And links for more info on backups and a Windows repair flash drive which you also should have.

---


---
title: "Uhoh - pooped my system trying to dual boot"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by charles-laferriere on 2017-09-02
Hello folks,
I've obtained a new pc (weeeh!) and wanted to dual boot with the windows version it came with (win7,home).
So I created a bootable usb with rufus.
Installation was succesful, it was SUPPOSED to have created a seperate partition.
Unfortunately, now theGrub only lists Ubuntu. 
And I'm a noobuntu, so its no fun.
Any ways to "revert"or roll back the install? Thanks..
C

---

### Post by yancek on 2017-09-02
You should have had several installation type options during the install, which one did you choose?
Did you shrink your windows partition from within windows to create unallocated space on which to install before trying to install Ubuntu?
Boot Ubuntu and open a terminal and run this command and post the output here:  sudo fdisk -l (Lower Case Letter L in the command).

---

### Post by charles-laferriere on 2017-09-02
Ok - 
I used the Ubuntu installer to get the disk partitioned. 
I tried reinstalling - I get a essage of detection that Ubuntu ANDwindows 7 are currently instlled on this machine. 
Here a SS of sudo fdisk -l
[http://imgur.com/a/ZbjNU](http://imgur.com/a/ZbjNU)

---

### Post by ajgreeny on 2017-09-02
Was Windows completely shutdown when you installed Ubuntu or was it in hibernation?  

Grub will only boot a working Windows OS and I think I remember reading that grub will not be able to do anything with the Windows OS if it is hibernated.
I have no idea about Windows 7 but I am aware that Windows 8 and 10 both use a hibernated state as their default when closing the OS; perhaps Windows 7 is the same.

Can you see and open the Windows partitions in Ubuntu's file-manager window?  If they are hibernated you will see an error message.

---

### Post by charles-laferriere on 2017-09-02
I can access the windows partition. No error. I clicked "Restart".

---

### Post by ubfan1 on 2017-09-02
Try running  sudo update-grub   in a terminal to see if that fixes the missing Windows in the grub menu.

---

### Post by charles-laferriere on 2017-09-03
YES YES YES!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
HERE A CUP OF FULL OF UBUNTU :D 
Thanks. tons

---


---
title: "How to I restore Ubuntu grub menu"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by surfcity_dad on 2008-05-05
I'm dual booting Ubuntu and Win 2000 on my box.  I somehow ended up corrupting Windows 2000, some sort of registry error.    I plan to reinstall Win 2000, how do I restore the Ubuntu grub startup menu after the Windows install?  I'm sure this is something simple, Ubuntu 8.04 is working great don't want to have to reinstall after I fix Windows.    I need Win 2000 for Quicken, been using it since '93.

I've looked in the prev posts but none seemed to answer this.

Any advice would be appreciated, 

Mark

---

### Post by Patb on 2008-05-05
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by bulldog on 2008-05-05
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by surfcity_dad on 2008-05-05
Thanks Bulldog!  I will do this evening.

Mark

---


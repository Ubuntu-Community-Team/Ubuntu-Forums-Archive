---
title: "dual boot.. already installed Ubuntu.. now want to install XP"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by joper90 on 2007-01-22
I nuke my machine and install Ubuntu, great move, but i still need XP. Now i know you can dual boot by installing XP first, but can i do it now I have installed Linux.

Im assume i can:
1) make a note of GRUB (or back it up)
2) install XP thrs trashing the MBR
3) restore (of live cd) the MBR for grub?

I have looked and googled, but most are XP install first.

cheers

---

### Post by bulldog on 2007-01-22
It depends a little where you installed ubuntu.
If you have it on the first partition,you can run into trouble when you want to install Windows.
But if you can install windows on the first primary,you can use the live cd to reinstall GRUB.
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

### Post by Jussi Kukkonen on 2007-01-22
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
that should cover it.

---

### Post by joper90 on 2007-01-22
Cheers guys.. its installed on the only disk and the only partition, i was going to resize the disk first, then use that for windows.. I assume that will work.

---


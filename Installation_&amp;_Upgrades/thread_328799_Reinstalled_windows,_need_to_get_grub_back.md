---
title: "Reinstalled windows, need to get grub back"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by hookem10 on 2006-12-31
I have just reinstalled windows to my C: partition, as i was dual-booting with windows xp and ubuntu.  Now, however, the MBR was overwritten and now grub doesn't load so i can't access ubuntu.  How do i get grub back to i can boot both windows and ubuntu?

---

### Post by bulldog on 2006-12-31
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
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


---
title: "help ith grub"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by aco on 2007-06-03
Ok people i need help

I had windowsXP and Ubuntu 7.04
Now i installed Vista over XP and i have lost grub os loading menu
How do i get it back

Thx

---

### Post by aco on 2007-06-03
Common ppl ow to return grub back

---

### Post by bulldog on 2007-06-03
Well you can do a little search on your own,can't you?
This is so many times answered,it should be easy to find.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
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

---


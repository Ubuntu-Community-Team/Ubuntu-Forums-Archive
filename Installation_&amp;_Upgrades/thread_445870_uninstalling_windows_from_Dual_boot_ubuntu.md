---
title: "uninstalling windows from Dual boot ubuntu"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by animeh on 2007-05-16
I have a Dual boot Windows and Feisty with the GRUB Menu. How can I unstall windows from my system without bothering Feisty?

any suggestions?

---

### Post by bulldog on 2007-05-16
You can just format your windows NTFS partitions in ext3 and use it as a data partition for ubuntu.

---

### Post by animeh on 2007-05-16
Thank You for your reply, I want to uninstall windows and re install windows later. Yes I do agree that Ubuntu is the best operating system, but I need windows to do some of my work and slowly will be going to Ubuntu.

Is there a way to uninstall the windows and re install windows with the dual boot?

---

### Post by bulldog on 2007-05-16
Nope but when you want to reinstall windows,there's no need to fomat the partition first.
Just boot from the windows install disk an choose the same partition as before to install,you can set the format option from there if you want.

When you installed windows,your grub is gone,you have to reinstall with the live cd.
Here's how to do that,
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

If you have any question about it,just ask.:)

---


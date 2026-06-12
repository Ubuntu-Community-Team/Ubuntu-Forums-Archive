---
title: "GRUB not booting on SATA hdd"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by nalbion on 2008-05-10
When I reboot after installing Mythbuntu I get as far as 
> GRUB Loading stage1.5.
and then it hangs.

I can boot using a live CD, or a KnoppMyth install, but I'd prefer to use Mythbuntu

---

### Post by bulldog on 2008-05-10
You can try to reinstall GRUB with the live cd.
When you get to the desktop open a terminal and type the following commands. 

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


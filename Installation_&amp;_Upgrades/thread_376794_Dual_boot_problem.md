---
title: "Dual boot problem"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by aindriuirl on 2007-03-05
Hi,
I recently started using ubuntu on my laptop.  I was just after getting it working and i reinstalled xp.  Now i don't get an option to boot ubuntu.  I was just wondering how i can get the option to boot ubuntu back.
Thanks,
Andrew

---

### Post by milton1 on 2007-03-05
you need to reinstall grub. search for 'reinstall grub' on this forum. Many, many posts.

---

### Post by bulldog on 2007-03-05
Install GRUB with the live cd,

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
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


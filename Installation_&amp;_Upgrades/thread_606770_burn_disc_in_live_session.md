---
title: "burn disc in live session?"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by tubunu on 2007-11-08
I've done something really stupid. 

Burned Gutsy to a CD, rebooted, clicked Install icon, chose to format my / partition and it turned out that there's some unexpected error so the install process hangs at 73%. Now I can't boot to Ubuntu because it's not installed (doh) and I can't boot to Windows because grub fails to load when I boot my PC. 

1. Is there a way to burn the image I have of gutsy on a new CD under live mode (using live gutsy CD)? I can't do it because I only have one CD burner and in it there's my live CD, so I can't unmount it to burn a CD. :confused:

or

2. How can I recover /boot/grub/menu.lst so that I can boot into Windows and burn gutsy to a CD from there? and begin installing gutsy from a new CD...

or 

3. help? :-(

---

### Post by bulldog on 2007-11-08
If you have a windows install disk go in the recovery console,logon to your windows and type fixboot and/or fixmbr

This make windows boot again grub will be gone.

---

### Post by tubunu on 2007-11-08
Thanks **bulldog**, fixmbr did it. 

However, I still think Ubuntu Live CD should be able to allow users to burn a disc in live mode. After all, live CD should be user friendly and help solve issues such as this one. Hardy Heron devs should take this into account.

---

### Post by bulldog on 2007-11-08
Yes,and I should have a Mercedes but I haven't :)

---

### Post by tubunu on 2007-11-08
Rrrright.. :)

Anyway, I burned gutsy .iso under Windows, installed the system, no problems. But.... now the grub is missing and all I get is Window$, which I don't use really.. Mmm how do I get grub back? sigh..

---

### Post by bulldog on 2007-11-08
You can reinstall grub with the live cd.
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
Next enter the command to install grub to the mbr[b] but be carefull here,if the find command returned (hd1,?)
the setup should be (hd1) not (hd0)!! [/b]
```
setup (hd0)
```
Exit the grub shell
```
quit
```

But by installing ubuntu it should have installed grub as well hmmm............I'll wait and see what happens.

---


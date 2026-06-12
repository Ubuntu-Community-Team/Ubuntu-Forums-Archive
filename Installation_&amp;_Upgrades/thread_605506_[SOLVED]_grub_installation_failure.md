---
title: "[SOLVED] grub installation failure"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by spaccount on 2007-11-07
Hi Everyone,
[INDENT]My first post! I tried installing gutsy last night, and am stuck at the last stage with a  *grub installation failure*. I'm trying to install this on a Dell Inspiron 6400 laptop. It is already loaded with XP. I had partitioned the disk before installing xp to make space for ubuntu. So this is how it looks.

[INDENT]
1. Primary Partition: 10GB - Windows XP 
2. Primary Partition: 6 GB - This is where I'm trying to install ubuntu, I do this by manually selecting the drive.
3. Extended Partition: This spans the rest of the harddisk and has been split into 4 logical drives[/INDENT]

I checked the Advanced screen for Grub install, there the field is populated with: hd0

Even after multiple install failures, I'm able to boot back into WindowsXP, which kind of makes sense as Grub could not install at all!

a. Any ideas? 
b. Also, do I need to restart the install from scratch to come to the Grub screen, or is there a way to skip to the last screen?
c. Perhaps some terminal commands?

[/INDENT]

Thanks!

---

### Post by stevie_velvet on 2007-11-07
as GRUB failed to install into the MBR, you might want to record & post the error message posted by GRUB

---

### Post by spaccount on 2007-11-07
Hi Steve,

[INDENT]Thanks for the prompt response. 

I just get a popup dialog with a message on the lines of:
[INDENT]** Grub Installation Failed. Fatal Error. ** [/INDENT]
After I press OK, the installation terminates and I'm back to my desktop.

Is there a way I can capture/view the detailed error log during the installation? Or perhaps an alternate way to run grub with some sort of trace on?
As of now, I reinstall ubuntu everytime I need to retry the GRUB installation :)  [/INDENT]

---

### Post by bulldog on 2007-11-07
You can try to install grub with the live cd,but I'm afraid you'll get the same error.
Maybe the super grub disk can help you further,
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

To install grub with the live cd:
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

---

### Post by Pumalite on 2007-11-07
How did you partition? Get a Knoppix Live CD and examine your system. You might have a 'recovery partition' at the front. Gparted Live CD would be useful too.

---

### Post by spaccount on 2007-11-07
> **bulldog said:**
> You can try to install grub with the live cd,but I'm afraid you'll get the same error.
Maybe the super grub disk can help you further,
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

To install grub with the live cd:
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


**Steve:**[INDENT] I tried the following, I get stuck at the second step: i.e. find /boot/grub/stage1
What next?[/INDENT]

**Pumalite:** [INDENT]I used WindowsXP boot CD to delete all partitions and then create the new structure. To do this, I removed all other partitions, including the default ones created by Dell, i.e. Media Center, Backup etc..

The new partitions are as mentioned: 
[INDENT]a. Primary1(WindowsXP), 
b. Primary2(For Ubunutu)
c.  Extended1(Containing 4 Logical Drives)[/INDENT]

 [/INDENT]

Please help!

---

### Post by bulldog on 2007-11-07
You get a location from the find command like (hd1,0)?
You have to use that location in the next command.
If you get no location from the find command,grub can't find your ubuntu install.

---


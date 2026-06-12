---
title: "Dual HD / Dual boot HD replacement GRUB Restore"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by lukon on 2007-01-14
In my dual hard drive, dual boot system, my Windows hard drive is failing. I need to replace it.

But my GRUB OS loader is also on the failing hard drive's MBR, right?

So when I put in my new hard drive, how can I re-install the GRUB OS loader also?

Here's more about the setup:

Primary Master HD (failing): Windows 98SE and the GRUB OS loader.

Primary Slave HD: Ubuntu Dapper Drake.

--------------------------

I've seen a thread about restoring GRUB, but I could not tell whether it would apply to my situation.

---

### Post by bulldog on 2007-01-14
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
Now Grub will be installed to the mbr

If you want to setup GRUB on the Ubuntu disk,you have to change setup (hd0) into (hd1) and make this the master boot disk.
You have the windows loader intact in case of trouble with GRUB.
If you do so you have to add two lines in your windows entry in menu.lst
like this,```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by lukon on 2007-01-16
Thanks Bulldog.

Unfortunately, I did not get a chance to try this process you offered me. It turns out that I made so many other hardware changes to my computer that I opted to simply re-install the OS's too.

I do, however, have two folow up questions for you.

1. How do I remove a deleted OS from GRUB?
If you decide to answer this one, please do so at the new thread I created for this question, here: [http://ubuntuforums.org/showthread.php?t=339973]("http://ubuntuforums.org/showthread.php?t=339973").

2. Can I move GRUB from the Windows hard drive to the ubuntu hard drive without using the ubuntu live CD? Can I instead do this from a normal ubuntu login to the ubuntu hard drive?

And regardless of method for moving GRUB from the Windows disk, will I need to restore the Windows disk MBR after the moving process?

---


---
title: "Need To Reinstall"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by rvickers on 2006-11-10
I have blown up my network configuration trying to get wireless to work. I dual boot with XP so if I put in the install CD and reinstall, is it going to install over the existing Ubuntu? Will it mess up my dual boot? Will it be the same as the original install, ie networking back the way it was and missing the packages I installed?
Thx

---

### Post by angryfirelord on 2006-11-10
If you try to do an install while keeping files, it would probably mess with your system. Doing a fresh install would delete everything.

However, before we do anything drastic :) , what drivers were you trying to install? If the drivers installed but wireless did not, you can always go to System-->Administration-->Networking to try and configure it.

---

### Post by rvickers on 2006-11-10
"System-->Administration-->Networking to try and configure it."

That's what's broke...
How do I do a fresh install?

---

### Post by angryfirelord on 2006-11-10
If you were tinkering with your networking and it broke, then a fresh install should fix that. However, all files will be lost so remember to back it up. Just put the Ubuntu cd in your computer, do a reboot, and follow the instructions. 

-Windows XP should not be affected. I have installed may different Linux distributions multiple times and Windows XP was not except for one time (then I said "to heck with windows, I'm just running Linux!"). 

I can guarantee a 99.999999999999999999999999999999% chance that WinXP will be ok.

---

### Post by rvickers on 2006-11-10
I reinstalled and network is back up but I now have 2 versions of Ubuntu. I would like to remove the old and utilize that disk space...

---

### Post by bulldog on 2006-11-10
Well you can use the Gparted live cd to do that.

Make a note on forehand so you know which partitions you want to delete.
Then you can add the free space to your existing install or create a new partition.
Gparted is found here [aprox 25MB] burn it on a cd and boot from it.
The rest is selfexplaining.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by rvickers on 2006-11-10
How can I tell beforehand which partitions contain the new Ubuntu?
Also, how can I cleanup grub? Thanks for the help, I'm on a tight time schedule and don't really want to do the research myself.
Thanks again...

---

### Post by bulldog on 2006-11-10
Well you can look in your menu.lst which partition you use to boot from.

You can just delete the entry's you don't use any more.

---

### Post by rvickers on 2006-11-10
I took my best guess and missed :rolleyes: . I used Gparted to clean up the linux partitions, XP fixmbr to fix grub and reloaded Ubuntu. Ubuntu is so easy to load that it's sometimes the fastest way to fix something. Think I'll stay away from wireless until I see some success on the forums.
Thx for the help... :D

---

### Post by angryfirelord on 2006-11-10
What wireless card do you have?

---


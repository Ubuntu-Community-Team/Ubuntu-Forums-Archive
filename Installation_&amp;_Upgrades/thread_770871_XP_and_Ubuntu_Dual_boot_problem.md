---
title: "XP and Ubuntu Dual boot problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by kg87 on 2008-04-27
Ok so basically, I had 8.04 and XP up a running on my laptop no problem. However after i restarted today, and tried to gain access to windows, the machine blacks out and restarts (bringing me to the OS selection screen?.. Vague i know, but thats all i've got. Xp is still there, and so is the ubuntu installation (i can boot into ubuntu). 

The hard disk is fine, and i've tried fixmbr from recovery console to no avail!

Please help!

---

### Post by A$h X on 2008-04-27
So what's shown on the grub boot screen? Does it still have windows as an option?

---

### Post by kg87 on 2008-04-27
Yes, Its still there, i can also hit return on it and it'll try to load, but other than that thats it. Also, It'll say "windows was not properley shut down" etc etc... and then restart, no matter what option is given

---

### Post by MasterSander on 2008-04-27
I don't know if the xp cds also have this option, but if you insert your vista installation disk you can select repair somewhere (with vista already installed ofc), perhaps that'll work? My vista got screwed up before and that solved it for me.

---

### Post by kg87 on 2008-04-27
Nah, I dont have the Vista Installation CD (although i am using the vista theme for compiz (ftw! :P).

Is there anything i could upload like my Grub.lst to aid a solution?

---

### Post by kg87 on 2008-04-27
Anyone?

---

### Post by dstew on 2008-04-27
It sounds like your Windows disk may have some errors on it. If you can boot a Windows recovery console, you can do **chkdisk** on the Windows partition. There are Linux tools that can also check a Windows file system. You can boot to Ubuntu, and on a command line enter```
sudo fdisk -l
```to get a list of your partitions. The command [fsck]("http://linux.die.net/man/8/fsck") can be used to check the filesystems on the partitions. You can only use fsck on an unmounted file system. I do not know if it can repair a ntfs partition, though. You might need to use the Windows chkdisk program for that.

---

### Post by kg87 on 2008-04-27
thanks for the suggestion i'll give that a go

---

### Post by kg87 on 2008-04-27
Nope, nothing, I hope its not goosed.. :(

---

### Post by kg87 on 2008-04-27
I think the problem would have been made easier if i hadn't of installed from windows (thinking "hey! what a great feature"), and installed on a separate partition

so it looks like im gonna have to format and start again, :@

---

### Post by ubutufan on 2008-04-27
Before reinstalling windows, try to locate the boot.ini file on the windows C: and post the results.
The way that I understand it from the (little) information you have provided is that there is something wrong with the windows boot.
You may use ubuntu to navigate to windows NTFS and locate the boot.ini file

---

### Post by kg87 on 2008-04-27
---- SUBJECT CLOSED ---- 

backing up as we speak, issue not resolved, 6hrs of valuable coursework time wasted :'(

---


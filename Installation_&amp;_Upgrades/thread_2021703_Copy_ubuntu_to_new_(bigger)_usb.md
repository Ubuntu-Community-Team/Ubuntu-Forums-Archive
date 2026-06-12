---
title: "Copy ubuntu to new (bigger) usb"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by sodifficult2day on 2012-07-09
I currently have installed Ubuntu 12.x.x  to a USB drive and just about have it all set up perfectly (apart from  HDMI sound (laptop speakers work fine) but that is a different matter)  but as this is now rather full I will like to copy the whole thing lock stock and barrel to a larger USB drive.  I guess it is not a simple a job as cut and paste?

---

### Post by zwygart on 2012-07-09
Nope, it isn't, but it's not much harder. 

I see one thing that could go wrong : the bootloader, since you can't copy paste it.

So what I suggest is create your partitions as you want (similar to the original), copy paste the content of the partitions. Then the interesting part. 

Plug your USB stick (may be both). 

Boot onto GRUB, (it's where you choose the OS), may be you need to press esc to see it. Press c to enter command line and then be carefull of what to do. 

type root (hd   followed by tab. This will show the avaliables disks). Choose the new one. 

then type
    setup(hdX)
where X is the number associated with the new USB key (the same as above of course). 

This should be all. 



Another way may be to just copy paste the entire key and then resize the partitions. 
Be carefull with this command : 

     dd if=/dev/sdb of=/dev/sdc

If your old is sdb and new sdc. Replace with the right letters. 
This will copy the entire USB key bit by bit. Then just resize the partitions with gparted or any other partitionning tool.

---

### Post by oldfred on 2012-07-09
dd is nicknamed Data Destroyer. Because any typo and you overwrite all the wrong data. So if you use dd be very careful to type it correctly.

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Also if you use dd it will mirror eveything including UUIDs. That is ok only if you do not want to have both drives plugged in at the same time as you cannot have duplicate UUIDs. Otherwise you have to change UUID and edit fstab with new UUID and reinstall grub to update all its UUID entries.

Just about any of the copy require some update, reinstall of grub or editing of fstab.

I prefer to just reinstall and copy /home over. If you have anything else like a list of installed apps or some system setting in /etc you still have old install to go back and copy it from. All data & user settings are in /home so that is most of what you what and a clean install makes it easy to set up system that works.


My backup procedure is just do do a clean install. So what I backup is what I am pretty sure I need.

Use rsync to copy.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---


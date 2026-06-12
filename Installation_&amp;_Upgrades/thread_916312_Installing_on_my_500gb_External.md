---
title: "Installing on my 500gb External"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Nicholas482109 on 2008-09-10
I'm running the live cd right now and I'm in the middle of the install. I want to make sure that i don't over write my MBR on my internal harddrive, again. In GParted I made a 11gb ext3 partition with a boot flag an a 480gb NTFS partition. I'm at Step 4, prepare partitions, part of the installation. When I have the ext3 partition highlighted and click forward it says no file system is defined. Should I edit it and change it to ext3 and put the mount point as /boot will everything run fine?

---

### Post by Pumalite on 2008-09-10
Plant a '/' where it says 'mount point'

---

### Post by Nicholas482109 on 2008-09-10
Just making sure, this laptop's internal hard drive will still boot windows after that?

---

### Post by Pumalite on 2008-09-10
At step 7, hit 'Advanced Tab' and change (hd0) for /dev/???; where ??? is your USB. Find out with:
sudo fdisk -lu

---

### Post by Nicholas482109 on 2008-09-11
I installed it twice, once telling it to install the boot loader on sdb, the drive, and once on sdb1, the partition it was installing to. Both times after GRUB loaded and i chose to boot Ubuntu it said something like Error 17, could not boot device. How can i fix this?

---

### Post by Pumalite on 2008-09-11
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Nicholas482109 on 2008-09-12
I'm looking at that now, going down each thing and seeing if it works. That's a lot of information though, can you narrow it down any more?

---

### Post by Pumalite on 2008-09-12
Take a look at these threads:
[http://ubuntuforums.org/showthread.php?t=606409](http://ubuntuforums.org/showthread.php?t=606409)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)
[http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146)
[http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263)

---

### Post by Nicholas482109 on 2008-09-13
I got it to work by removing my internal drive and installed the boot loader to hd0, everything is working fine, thanks for those links. Using [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") I tried to do it the automatic way but i don't have NTFS Configuration Tool in my system tools menu. When I typed in the code it gives to open it in the terminal it loaded for a second then asked me for my password but did nothing else. What's up with that?

---

### Post by Pumalite on 2008-09-13
Explain better what you did.

---

### Post by Nicholas482109 on 2008-09-13
I want to view my laptop's internal 160 gb drive. I typed into the terminal: gksudo ntfs-config  .   The mouse pointed changed to loading then a new command line appear and no window came up. I then went to so launch it from the menu applications>System tools> but the only app in there was ubuntu tweak which i just downloaded.

---

### Post by Pumalite on 2008-09-13
sudo mount -t ntfs-3g /dev/??? /media/windows
??? is your Windows partition
Have to make the mount point:
sudo mkdir /media/windows

---

### Post by Nicholas482109 on 2008-09-13
ok I'll try that next time I go into ubuntu, but why can't I see the NTFS configuration tool in the menu?

---

### Post by Pumalite on 2008-09-13
Maybe you have to install it.

---

### Post by Nicholas482109 on 2008-09-14
Ok so I got everything running but a few last things to work out. How can I get my Trash in my AWN? How do I add awn to the start up list? And is there anything I can put an icon into the awn to show all the workspaces in the desktop cube? Also the weather screenlet doesn't seem to be working even after I put in my zip code, does it need a weather location code?

---

### Post by Pumalite on 2008-09-14
Make a new thread with an appropriate tittle.

---


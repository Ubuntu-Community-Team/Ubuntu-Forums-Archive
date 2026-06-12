---
title: "Ubuntu - Deleting home folder , renaming /home.backup"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by gauravpuri.bits on 2013-10-27
I am an amateur and I created the ubuntu virtual disk using wubi. Something wrong happened and now my data is completely lost  and is stored in a backup folder /home.backup. 

The wubi guide [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) suggests me to delete /home and rename /home.backup to /home. 
When I try to delete /home it says that the resources are in use and  i can't delete. Please help . i have a project submission and i am stuck in middle of nowhere. 


Thanks

---

### Post by fantab on 2013-10-27
What version of Ubuntu are you using?

First of all close all the running programs/applications and copy /home.backup to an external device.

Try renaming the present /home folder to /home.bak or /home.old. If it works, then rename /home.backup to /home. And now you can delete /home.bak.

If that doesn't help then boot with Ubuntu DVD/USB, 'Try Ubuntu without installing', open File explorer, plugin the external device on which you have copied /home.backup and rename the folder as /home and access your data.

Hope it helps.

---

### Post by gauravpuri.bits on 2013-10-28
When i try to rename it shows the resource drive in use.

---

### Post by gauravpuri.bits on 2013-10-28
Ubuntu 12.04

---

### Post by fantab on 2013-10-28
> **fantab said:**
> 

If that doesn't help then boot with Ubuntu DVD/USB, 'Try Ubuntu without installing', open File explorer, plugin the external device on which you have copied /home.backup and rename the folder as /home and access your data.



What happens when you do the above?
WUBI is not a real dual-boot. Wubi was meant for windows users to "Try" ubuntu for a longer period of time. But it was meant for trial. Wubi is not being developed actively, hence on the newer versions of Ubuntu WUBI is either not an option or it doesn't work well. It has problems.

I suggest you install Ubuntu to its own partition and set up a true dual boot.

---

### Post by bcbc on 2013-10-28
> **gauravpuri.bits said:**
> Something wrong happened and now my data is completely lost  and is stored in a backup folder /home.backup.

I assume you were running the script posted on the WubiGuide wiki that allows you to create a separate /home. And that your old home is on /home.backup as you say, which means all your data is there (not "completely lost"). I suggest you take the time to backup this data, preferably onto a separate USB stick or partition (or even under the Windows /host) so you can access it from Windows and restore it later.

That should be the first step, before trying to delete /home and rename /home.backup. On that note, you can probably unmount the new /home first rather than trying to delete it. If the script did it's job then it would have created a new virtual disk (/host/ubuntu/disks/home.disk) and added an entry to /etc/fstab.

So try:
1. sudo umount /home
2. sudo mv /home.backup /home
3. Edit /etc/fstab and comment out the new line: #/host/ubuntu/disks/home.disk   /home ....

But do this AFTER backing up your data. And if you need to resize Wubi, you can try a more userfriendly script here: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---


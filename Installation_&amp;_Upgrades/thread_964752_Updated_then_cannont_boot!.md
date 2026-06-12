---
title: "Updated then cannont boot!"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by tom91 on 2008-10-31
I am (was) runnuing Ubuntu 7.04. I decided the time had come to upgrade to a newer version. I started by making sure my existing package was up to date, so I downloaded and installed all the outstanding updates (there were a lot). When I rebooted, I can no longer boot Ubuntu from GRUB. I just get this error:
Error 17: Cannot mount selected partition
Windows XP (on a separate HDD) still boots fine.
I've backed up all my data, so I can do a fresh install of Ubuntu, but I would prefer to recover my existing OS if poss. Any Ideas? Thanks.

---

### Post by caljohnsmith on 2008-10-31
Sounds like it could be simple problem with your Grub's menu.lst. Try this first: on start up when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If that doesn't work, try X = 1 or 2, or however many drives you have minus one. Based on the info you gave, one of those combos will most likely boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

If it doesn't work, then using a terminal in your Live CD (applications > accessories > terminal) please post:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by tom91 on 2008-11-01
Thanks. I just had to change the X from  to 0, now it boots no problem :)

---

### Post by caljohnsmith on 2008-11-01
I'm glad to hear it worked. There's one last detail though that I think you'll want to take care of: probably the reason you had the booting problem to begin with is the "# groot=(hdX,Y)" line in your menu.lst is incorrect, so when you upgraded and the updgrader ran "update-grub" to update your menu.lst, that's probably what messed up your menu.lst. I would recommend checking that line and correcting it so you won't have problems in the future when you get a kernel upgrade. So if you open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And check that the "# groot=(hdX,Y)" line uses the (hd0,Y) that worked to boot Ubuntu. And if you haven't done it all ready, you would also want to change all your Ubuntu entries to use the new (hd0,Y) also. 

Anyway, cheers and have fun. :)

---


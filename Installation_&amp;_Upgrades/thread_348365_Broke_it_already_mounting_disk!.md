---
title: "Broke it already mounting disk!"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by chip616 on 2007-01-28
Just installed 6.06 and did the whole update.  Had it running about 2 minutes and I broke it.

I'm going from memory, as I can't get back into the system.

On the Ubuntu menu at the top left, I checked system at the top, and went to disks.  It showed in the left pane the disks on my machine, including hb1, which I clicked, and was trying to mount.  In the right pane there was something there with regard to mounting, and it asked for a mount point, which I gave as /home, and then enabled the mount with the green circular arrow underneath.  I assumed that I would get a mount at /home/hdb1 for the second disk.

I closed the window, and now nothing works.  Clicking a menu item says that the menu item cannot be found.  Rebooting takes me as far as the login screen.  When I try to log in, it says that /home/chip was not found.

Suggestions?

Thanks.

---

### Post by aysiu on 2007-01-28
Well, I don't know the best way to fix this, but I can tell you what went wrong. You wanted to mount the disk as /home/hdb1, but you ended up mounting it at /home. So this means when Ubuntu is looking for what *used* to be in /home (like /home/chip), it's finding nothing.

You need /home in order to log in properly.

You could probably fix this by booting into recovery mode and editing your /etc/fstab or using a live CD to mount your partition and manually edit the /etc/fstab file, but you'd have to know what you're doing.

My best guess would be to boot into recovery mode, type ```
cp /etc/fstab /etc/fstab.bad
nano /etc/fstab
``` This will allow you to edit the /etc/fstab file. In it, you should find some lines that look like this: ```
#/dev/hdb1
UUID=f0093b94-ab75-4738-9144-9d1a9d6163fd /home ext3 defaults 0 0
``` Obviously the UUID will be a bit different, but I hope you get the gist. Change /home to /home/hdb1 and then save (Control-X, Y, Enter). Finally, create that mount point: ```
mkdir /home/hdb1
``` and reboot ```
reboot
``` If that doesn't work, we'll try something else.

---

### Post by bernied on 2007-01-28
OK - isn't linux fun?

So what you've probably done is to mount hdb1 over the top of your home directory, so all your settings, menus, desktop configuration is not accessible - but it is not destroyed!

If you can get a terminal (try Alt-F2 and type 'gnome-terminal'), then use the command 
```
sudo umount /dev/hdb1
```
This may not work because various programs may be trying to access /home

Does this work? Note this is not a permanent fix, the system will probably try to mount it again.

---

### Post by bernied on 2007-01-28
Ah yes, you can't login, so you can't get a terminal.

---

### Post by bernied on 2007-01-28
Can you boot into recovery mode?

You want to edit fstab and remove the line with hdb1 (or just edit it so it mounts in a more sane place)
```
nano /etc/fstab
```should get you an editor in recovery mode.

---

### Post by aysiu on 2007-01-28
> **bernied said:**
> Ah yes, you can't login, so you can't get a terminal.
If you boot into recovery mode, you can log in.

By the way, at this point ```
nano /etc/fstab
``` is a **very** bad idea!

Do either ```
cp /etc/fstab /etc/fstab.bad
nano /etc/fstab
``` or ```
nano -B /etc/fstab
``` Since your system is already screwed up, editing a system file before you make a back-up of it would be inviting more potential screw-ups.

---

### Post by bernied on 2007-01-28
Yes, ok, aysiu is right. Be more careful than I am.

---

### Post by chip616 on 2007-01-28
Thanks, all.  I might just re-install, as I have zero invested other than the time it took to download that mountain of updates.  However, I can let the machine churn away on that on its own time.  :)

So, if I understand this right, it mounted hdb1 _*AS*_ /home instead of _*IN*_ /home.  This is not what I am used to in Linux.  Things usually happen one directory down from what you specify.  I understood mount point, not full mount name.

As the data on hdb1 is shared data among all accounts on the machine, and in fact, among all the accounts on my home LAN, I have had it mounted as /home/common on all my other Linux machines.  I assume that next time I try this, I should try mounting it as /home/common rather than just /home, correct?

By the way, I have been mounting it in /home as that is one of the directories that gets preserved when doing an upgrade (on other distros, at least).  /home/common is a data directory that is mirrored on several of my machines and kept synchronized through the use of rsync.  On this machine, it happens to physically reside on a separate hard disk.  On some of my other machines, it physically resides at /home/common.

Thanks.

---


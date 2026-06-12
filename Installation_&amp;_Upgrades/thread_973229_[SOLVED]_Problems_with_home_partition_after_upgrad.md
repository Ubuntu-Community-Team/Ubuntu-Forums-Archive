---
title: "[SOLVED] Problems with home partition after upgrade"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by shortylonglegs on 2008-11-06
I have a separate partition for home to make backups and restoring easier, but ran into a problem now.  When I first boot up, it puts me into a maintenance shell, where I need to manually mount this partition: ```
sudo mount /dev/sda3 /home
```
I also get an error when I log in about not owning the permissions to my home directory.  This all happened when I tried to restore my home partition after losing it during my upgrade to 8.10.  Is there an easy way to fix this?  I think I have to change fstab to reflect the new uuid of my home partition, but I don't know how to find the uuid.

---

### Post by shortylonglegs on 2008-11-06
I ran: ```
cd /home/
chmod 644 ./[my username]
```based on the error that pops up when I tried to log in, so the error about my home directory doesn't come up anymore, but I now get an error: > Could not update the ICEauthority file /home/[username]/.ICEauthority and > There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256) and the screen just stays black when I try to log on.  If I recall I had been told to delete the ICEauthority file when I ran into this before, but I'm not sure so I don't want to try it.

---

### Post by Happibun on 2008-11-08
Hi,

It looks like you are getting the same problems as I am. I'm afraid I can't give you a complete solution yet because I am still blundering about in the dark with this, but I do have a thread here: [http://ubuntuforums.org/showthread.php?t=970879](http://ubuntuforums.org/showthread.php?t=970879) Perhaps it is some consolation to know that you are not alone.

To find the UUID of your home partition, you might want to try putting this in to a terminal window - It will list all of the partitions on your hard drive.

> sudo blkid -c /dev/null

Oh yes, I also had the ownership of the home folder problem that you mention in your first post. That got solved for me here: [http://ubuntuforums.org/showthread.php?t=971110](http://ubuntuforums.org/showthread.php?t=971110) by Sisco311. These lines typed in to a terminal window one by one did the trick.

> sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrcThe commands are restoring the default settings (permissions and owner) on your home folder. 

*chown -R $USERNAME: $HOME* - change the owner of home folder(/home/username) to your user.

*chmod 755 $HOME* - set the permissions of the home folder to 755 (read/write/execute for owner, read/execute for group and others)

*chmod 644 $HOME/.dmrc* - set the permissions of the .dmrc file to 644 (read/write for owner, read for group and others)

more about permissions here:[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I hope that helps.

---


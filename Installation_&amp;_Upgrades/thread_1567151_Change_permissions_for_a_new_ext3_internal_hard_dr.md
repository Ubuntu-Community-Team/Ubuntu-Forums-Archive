---
title: "Change permissions for a new ext3 internal hard drive"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Lordanum on 2010-09-03
Hello, i'm a relatively new user of Ubuntu (about a year now) and love it.

I've already installed 2 x 1TB drives at the end of last year with success, but now i am trying to install a 2TB drive and having problems getting permission to read/write.

It installed and formatted (via Gparted) fine. I tried a couple of commands in the terminal to change the permissions to me, or my group, but to no avail.

Could someone help, as i'm stuck?

---

### Post by ajgreeny on 2010-09-03
You will need to edit and add a line to /etc/fstab and also use the **chmod** or **chown** command in order to get the drives mounted read/write for users.  You do not say how you formatted them, fat32, ntfs or ext3/4, but assuming they are ext3 or ext4 the line will need to be similar to this.
```
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /mnt/ubuntu ext4 defaults,relatime 0 2
``` The UUID is for the partition on the drive which you can get from command ```
sudo blkid
``` The mount point will be needed before you try to boot with this line present, or you will get an error message, and you can mount it where you wish, the /mnt/ubuntu is just an example. Once mounted you will need to use the command **chown** or **chmod** but exactly what you need to set with those commands will depend on the system, possibly ```
sudo chmod -R 777 /mnt/ubuntu
```which will give everybody read/write/execute permissions on that folder, ie that drive.

If you want to limit permissions to some other users the command can be changed.

---

### Post by Lordanum on 2010-09-03
All the drives that are installed are ext3. 

I have a 1.5TB for the main drive, with 2 x 1TB drives for storage (films / music).

This extra drive is for extra storage and such.

All these were formatted as primary, so can the new one be as primary or should it be extended/logical? 

Sorry to ask, but i'm still trying to get my head around Linux workings, as i've been a Windows user for many years.

---

### Post by oldfred on 2010-09-03
Some good info if more than one user.

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---


---
title: "/home is being corrupted under Ubuntu 18.04 (maybe related to OpenDesktop/xdg?)"
date: 2018-09-19
forum: Installation &amp; Upgrades
---

### Post by digitijit on 2018-09-19
I had never seen the following problem until installing Ubuntu 18.04 (and Mint 19): The permissions and ownership of non-hidden files in /home are being changed to "unknown" after restoring backup files after re-installation of Ubuntu.  This happens repeatedly; I think I am up to my 5th or 6th re-installation attempt.  Initially I suspected malware, but clamav scans of my home backup find nothing.  The changes in ownership/permission seem to happen after use of either chown or chmod, but that may not always be the case.  Valid ownership and permissions cannot be re-created, even by root.  Hidden files are spared that death.

Also, I noticed that any non-hidden files at the base of /home/username are moved to /home/username/Documents or /home/username/Public.  Regardless, the ownership and permissions are eventually always corrupted.  That makes me wonder whether the problem might be related to OpenDesktop and the xdg files.

A posting by samir038 on June 7 2018 seems to describe a similar problem, but no solution was posted.  One's /home should never be violated -- ever.

Any tips on how to protect my /home from file relocation and corruption of ownership and permissions?

---

### Post by oldfred on 2018-09-19
You must be backing up to FAT32 or NTFS which do not support Linux ownership & permissions. 
You should be backing up to ext4 or other Linux format and use commands that preserve ownership & permissions.

       Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER


[LIST=1]
[*]chmod 644 /home/$USER/.dmrc
[/LIST]

---

### Post by digitijit on 2018-09-19
All backups were to an ext4 filesystem, and ownership of all permissions is preserved there.  The correct permissions and ownership appear when /home is first restored, but they end up getting corrupted later---sometimes days later.

---

### Post by digitijit on 2018-09-19
And it gets even more puzzling:  I extracted /home a tar backup on the (ext4) backup drive.  The extracted files had owner $USER and various permissions.  I then did sudo chown -R $USER:$USER * followed by sudo chmod -R 644 * just to make sure everything was correct.  Initially everything looked good.  However after returning to that copy of /home all files have owner "unknown", permissions "unknown" and date modified "unknown",  Correct ownership and permissions cannot be recovered from those files using sudo chown or sudo chmod, respectively.

---

### Post by oldfred on 2018-09-19
If you are using -R parameter for recursion, you must be very careful on path. If you modify any system files, reinstall is about the only alternative.
One user post he accidentally added a space and then /home become / home and system only saw / so did entire system.

---

### Post by digitijit on 2018-09-20
However, "chown -R $USER:$USER *" and "chmod -R 644 *" executed from /home should be fine.  

I have never seen owner="unknown", permissions="unknown", and the fact that those files cannot be recovered seems very bizarre to me.  Can anyone explain that and tell me either how to prevent it from happening or how to set sane ownership and permissions on those files?

---

### Post by Claus7 on 2018-09-21
Hello,

haven't faced such an issue, yet, if creating a new user, do you observe the same thing? 

Regards!

---

### Post by digitijit on 2018-09-23
Thanks to responders for patience.  The problem was lack of execution permission on /home/$USER.

---


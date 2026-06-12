---
title: "Problem with file permissions after upgrade"
date: 2019-08-03
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2019-08-03
I recently upgraded to Ubuntu 19.04. Before the upgrade I copied my /home to another disk drive to keep it safe. Then after the upgrade I recopied the /home bask to the new installation. I am not sure what happened but now my entire /home has all the permissions changed to root. Is there an easy way to change the ownership and permissions back to the way a normal installation should be, without having to change each individual file? I tried changing the permissions on the directories but all the files within them are still read only.

---

### Post by TheFu on 2019-08-03
Unix backups need to include the file and directory permissions.  
There is no way to put them back, if you didn't save them.

But we can make most of the files have "reasonable" permissions, though a few will not and that will break some things.

```
sudo chown -R $USER:$USER  $HOME
```
that exact command, so do what you need - mostly.  ssh will not work and gpg and the keyring might not work anymore either.
On a multi-login Linux, you'll need to do that for every different userid (can't use USER variable) and you cannot use the $HOME variable, since it won't be correct for other userids.

Live an learn.

---

### Post by oldfred on 2019-08-03
Some more info. Some specific files may need settings changed.
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
       .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---


---
title: "Upgraded to Ubuntu 15.10 and can't access files from previous user"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by Jeremy_Childress on 2016-01-06
I upgraded from 14.04 to 15.10. I chose the option upgrade and keep existing files. Now my wife's pictures don't seem to be accessible. I did change the user name of the computer from Lorita to Jeremy. Is there any way to recover these files, pitures, documents, videos, and music, maybe even old desktop files? I've tried running in recovery mode, restore option from ubuntu-tweak, I'm at a loss. Can somebody please help me?

---

### Post by oldos2er on 2016-01-06
You added a user, or changed the name of a single user account? I'm assuming no backups of these files exist?

---

### Post by oldfred on 2016-01-06
Do you still have a /home/Lorita? 
Or did the user name change erase that. If you have kept the same user name then it should have kept data.

Always best to have good backups especially when doing major system changes.

---

### Post by Jeremy_Childress on 2016-01-06
No, there's no backups. When installing the upgrade I named computer Jeremy instead of my wife's name. Now I can't access the previous files. Not sure what to do to recover them. Old computer/user name was Lorita. During Upgrade I changed it to Jeremy. Is there a way to recover the files, change the user name to restore priveleges to these files or anything?

---

### Post by Jeremy_Childress on 2016-01-06
I changed the file path to /home/lorita and sure enough the files were there. Now I feel dumb for not trying this before. Thanks oldfred!! Problem solved. I just need to change back to old user name or move the files to new one, either way problem solved. You're aces, thanks!!

---

### Post by oldfred on 2016-01-06
You may have to change ownership and/or permissions to access those files. They are Lorita's currently.

Example is you, so change example, probably this?
 sudo chown -R $USER:$USER /home/lorita
sudo chmod -R a+rwX,o-w /home/lorita

Since we managed to close the barn door before the horses left, you still have a chance to start a good backup procedure. Trying to recover data after the fact is extremely time consuming and not all data can be recovered.

---

### Post by Jeremy_Childress on 2016-01-06
I just did a cut and paste of all files from /home/lorita to the /home/jeremy folders. Music to Music, Pictures to Pictures, Desktop to Desktop, etc. I already had permissions to do this, I just had to change the file path to find them as the new user was made administrator, and the old one saved as mere back up files, per the options I was given, and clearly misunderstood the first time. I just needed a good refresher course on how to accomplish this. I will actually do a manual back up on my external hard drive to prevent this from happening again. I'll be sure next time an upgrade is necessary every file is backed up on an external source in case it needs to be restored. Thanks man!!

---

### Post by Bucky Ball on 2016-01-06
Good news. Please see first link in my thread to help others. This will not close the thread to further discussion. :)

---


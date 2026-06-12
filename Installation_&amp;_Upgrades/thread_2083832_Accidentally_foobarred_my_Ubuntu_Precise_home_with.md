---
title: "Accidentally foobarred my Ubuntu Precise /home with a Fuduntu install - reinstall?"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by blackbird34 on 2012-11-13
Hi
Just installed fuduntu (2012.4) to a partition of my computer alongside Ubuntu. I think I committed a fatal error however by telling fuduntu to use the same /home folder as Ubuntu (which has separate /home and / partitions). After my first Fuduntu update (it's a rolling release which takes application and kernel updates as they come) I restarted in Ubuntu 12.04.1 LTS, filled in username/password, but could not log in.
LightDM  simply returned me to the login screen. I suppose fuduntu must have modified some config files...

How can I revert them and manage to login properly again? Would reinstalling make Ubuntu wipe the config files to make them to its own liking again?

Thanks:guitar:

---

### Post by ajgreeny on 2012-11-13
Did you use the same username when you installed fuduntu as you have in ubuntu?  If it was not different it is possible that fuduntu may have changed permissions of all the files in /home.

However it may be worth starting ubuntu in recovery mode, assuming you can, then mounting the ubuntu partitions as read/write instead of read only with ```
mount -o rw,remount /
```though as it is the /home partition, not root that is at fault, you may not even need that command.

You can then try changing ownership of the /home partition back to your ubuntu username with ```
chown -R username:username /home/username
``` and also permissions to the ubuntu default with ```
chmod -R 755 /home.#/username
```  It is also worth looking for the UID of the fuduntu user to see if that is different from the ubuntu UID of 1000 for the first user, though I am not sure if or how you can change that back; perhaps the **chown** and **chmod** commands will do it for you.

This is, indeed a salutary lesson not to try and share the same user in a /home partition; use the same partition by all means, but make sure you have a different username and therefore home folder within /home for each OS

---

### Post by blackbird34 on 2012-11-13
> **ajgreeny said:**
> Did you use the same username when you installed fuduntu as you have in ubuntu?  If it was not different it is possible that fuduntu may have changed permissions of all the files in /home.
Yes I did...

> **ajgreeny said:**
> However it may be worth starting ubuntu in recovery mode, assuming you can, then mounting the ubuntu partitions as read/write instead of read only with ```
mount -o rw,remount /
```though as it is the /home partition, not root that is at fault, you may not even need that command.

You can then try changing ownership of the /home partition back to your ubuntu username with ```
chown -R username:username /home/username
``` and also permissions to the ubuntu default with ```
chmod -R 755 /home.#/username
```  It is also worth looking for the UID of the fuduntu user to see if that is different from the ubuntu UID of 1000 for the first user, though I am not sure if or how you can change that back; perhaps the **chown** and **chmod** commands will do it for you.

This is, indeed a salutary lesson not to try and share the same user in a /home partition; use the same partition by all means, but make sure you have a different username and therefore home folder within /home for each OS

I'll have a quick go at that. I could login to a tty on my Ubuntu, but no X, so I can run commands.
The 'id' command says the UID is 500 on fuduntu.

I found this help page [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/) so would the command ```
usermod -u 1000 nad
``` be correct? And can I run that from inside fuduntu without making a horrible mess, thus having the same UID on Fuduntu and Ubuntu?

---

### Post by ajgreeny on 2012-11-14
Sorry, but I am as lost as you when it comes to the safety of changing the UID in either Ubuntu or Fuduntu, the latter of which I have heard of but never looked at or used.

If Ubuntu is you main OS, try changing the user UID in fuduntu to 1000 the same as Ubuntu to see if that helps.

Here, I shall have to leave this to others as I am now out of my depth.

Good Luck.

---


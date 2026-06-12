---
title: "[SOLVED] /home doesn't feel like home"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by YaacovI on 2008-07-16
I'm running 8.04 and I followed the instructions for creating a /home partition post-install at:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

When I tried to login, I got errors saying that the .dmrc file needed to have perms 644 and also that there was a problem accessing .ICEauthority . I used a Failsafe Terminal login and noticed that the owner of ~ and many of the files in it was root rather than my user. For each user on the system, I went to the home directory and did:
```
# sudo chown -R username *
# sudo chown -R username .*
# sudo chmod 644 .dmrc
# sudo chmod 644 .ICEauthority

```
I then checked using ls -l that the modifications had happened.
Now I can log in fine and I see the normal files on the desktop. However, the settings for various apps are missing. When I start firefox, it doesn't have my extensions, bookmarks, homepage, etc. When I start evolution, it asks me to create an account. The GNOME menu and theme settings are back to defaults.

I'd rather not have to go through app by app and restore these, especially when I know that the problem isn't specific to the app, but I can't figure out what else to do. Any suggestions?

Thanks,
Yaacov

------
The commands above are wrong, and should actually be:
```
# sudo chown -R username .
# sudo chmod 644 .dmrc
# sudo chmod 644 .ICEauthority

```

---

### Post by DGortze380 on 2008-07-16
Sounds like there are still some hidden files/directories in your home directory with the wrong permissions/owner

---

### Post by YaacovI on 2008-07-16
Thanks for the suggestion, Dan. I tried:

```
$ find ~ ! -user username
```

and the output was blank. I tried it again substituting the username of a different user and I got a list of the files in the ~ directory tree, both visible and hidden, so it looks like the owner of the files is correctly set. The perms vary from file to file, but I have at least read and write perms to every file in the ~/.mozilla/firefox tree. at least.

---

### Post by DGortze380 on 2008-07-16
> **YaacovI said:**
> Thanks for the suggestion, Dan. I tried:

```
$ find ~ ! -user username
```

and the output was blank. I tried it again substituting the username of a different user and I got a list of the files in the ~ directory tree, both visible and hidden, so it looks like the owner of the files is correctly set. The perms vary from file to file, but I have at least read and write perms to every file in the ~/.mozilla/firefox tree. at least.

try 

ls -al /home/username

(obviously substitute your home directory for /home/username)
that will give you a clearer view of everything in your home directory and its owner group and permissions.  Other than that I've got nothing for you. Sorry. Good Luck.

---

### Post by logos34 on 2008-07-16
you could try chmod 700 or 755 

[http://ubuntuforums.org/showpost.php?p=2393543&postcount=9](http://ubuntuforums.org/showpost.php?p=2393543&postcount=9)
[http://ubuntuforums.org/showthread.php?t=371052&highlight=.dmrc](http://ubuntuforums.org/showthread.php?t=371052&highlight=.dmrc)

---

### Post by YaacovI on 2008-07-17
Dan and logos34, thanks for the suggestions.

I figured out what the issues were. First, 
```
# sudo chown -R username *
```
should have been 
```
# sudo chown -R username .
```
Note that the last character is changed from an asterisk to a dot. 

When I thought I was chowning the various user home directories, I was actually chowning everything, so when I did it for the second user, it overwrote the previous user. 

I then deleted the home directories, restored from backup, ran the chown with the dot and all was happy again.

---

### Post by Rocket2DMn on 2008-07-17
Try doing the user AND the group (both are your username), then set permission of the /home/username directory to 700
```
sudo chown -R <username>:<username> /home/<username>
chmod 700 /home/<username>
```
Obviously, substitute your login name for <username>, without those brackets.

---


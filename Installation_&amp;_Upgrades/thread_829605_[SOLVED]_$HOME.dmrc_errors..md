---
title: "[SOLVED] $HOME/.dmrc errors."
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by FAJALOU on 2008-06-15
Hi all
I recently put my /home directory onto a different partition, and it is working well.  The only problem I am having is that, at login, I get an error stating;> The File $HOME/.dmrc is being ignored.  This file saves your default language and session.  Make sure that this file is owned by the user and has 644 permissions.  Also make sure that Home is owned by user.(Note these are not the exact words, but really close, I can write it word for word if necessary).

I have already tried ```
chown louie $HOME/.dmrc
``` and also ```
chmod 644 $HOME/.dmrc
``` and no errors are shown, but I still get the error.  Any thoughts?  I can try anything needed.

---

### Post by Partyboi2 on 2008-06-15
try booting into recovery and
```
chown -R username:username /home/username
``````
chmod 644 /home/username/.dmrc
```reboot
* Replace username with your actually username.

---

### Post by FAJALOU on 2008-06-15
I have already tried these, and I can log in fine, but the dmrc just seems to not be working.  Are you sure that this will help, because I have already done it.  Also I have the complete quote from the error message if it is wanted/needed.  Thanks

---

### Post by FAJALOU on 2008-06-15
Solved, i needed to change the home directory to 700 permissions.  Now no error.  Thanks all.```
chmod 700 /home/[username]
``` For future references.

---


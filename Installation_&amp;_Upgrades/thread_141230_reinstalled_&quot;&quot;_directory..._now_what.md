---
title: "reinstalled &quot;/&quot; directory... now what?"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by macluvjay on 2006-03-07
ok, so I messed up permissions on my root partition.  newb, blah, blah, blah, newb.  I know.  Anyway, at least I kept my home directory on another partition.  Now when I log in i get this message:
"Your $HOME/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions."

so I do this:
ls -la

shows my ~/.dmrc file as -rwxrwxrwx and owned by "MY_USER_NAME" and "MY_USER_GROUP"

Seems right, but my instict is still to:
sudo chown MY_USER_NAME: /home/MY_USER_NAME
and
chmod 644 ~/.dmrc

Any suggestions are greatly appreciated

---

### Post by Sutekh on 2006-03-07
[QUOTE=macluvjay] -**rwxrwxrwx** and owned by "MY_USER_NAME" and "MY_USER_GROUP"

Seems right, but my instict is still to:
sudo chown MY_USER_NAME: /home/MY_USER_NAME
and
chmod 644 ~/.dmrc

Any suggestions are greatly appreciated[/QUOTE]
Your instinct is right.

Those permissions (rwxrwxrwx) are 777 not 644, so ```
sudo chmod 644 ~/.dmrc
```
I did some digging and it seems that this problem could also require
```
sudo chmod -R 755 ~/
```
[http://forum.deviantart.com/os/unix/528986/]("http://forum.deviantart.com/os/unix/528986/")

---


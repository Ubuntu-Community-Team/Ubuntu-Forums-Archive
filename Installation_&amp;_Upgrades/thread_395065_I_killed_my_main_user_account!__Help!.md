---
title: "I killed my main user account!  Help!"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by blueman2 on 2007-03-27
I made the mistake of changing my main user account's location to /root.  Now I can not longer log on.  It gives me a message about file access.  I can still log on as root, but under root there is no option for user managment!  

Help!

---

### Post by afilonov on 2007-03-27
You can manually edit /etc/passwd file under root. Find line with your username, change /root to /home/username.

---

### Post by blueman2 on 2007-03-27
Uh, embarassed, but found a solution.  While user management does not appear under System-Administration drop down, the file to run is still there under /usr/bin.  Ran the file and was able to re-edit my user profile back to normal.  

All is well....

---


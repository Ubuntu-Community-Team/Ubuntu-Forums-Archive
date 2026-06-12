---
title: "Installation user cannot perform sudo"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by philip2007 on 2007-11-17
Hi 

I'm completely new to Linux and is trying out Ubuntu 7.10 Server edition with LAMP.

Downloaded ISO file from website, burnt to CD and installed to PC. Everything went smoothly. 

After installation, I log in using the username created during installation.  Login was successful.  However, when I executed the command

sudo passwd root, I got error saying username is not in the sudoers file.

When I run command 

sudo apt-get install, I got same error saying username not in sudoers file.

A check in /etc/group revealed that the username I created during installation was not in the sudo group

What is wrong and what can be done to correct that problem ?

Thanks in advance for any advice

Philip

---

### Post by Jussi Kukkonen on 2007-11-17
Your user should be in group 'admin' and */etc/sudoers* should have this in it:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Ans you should be able to change those if they're incorrect by booting in to a root shell, e.g. like described here: [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by philip2007 on 2007-11-19
Thanks a lot. You advice helped solved my problem

---


---
title: "sudo user /home change location"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by linuxlady2714 on 2005-08-25
I'm configuring ubuntu desktop machines as ldap clients in a lab.  When the user logs in, the machine is suppose to automount the user's /home directory.  But in the installation, the sudo user's home directory is in /home.  I tried to move the directory, but when I did, I couldn't run the package manager.

What can I do so the sudo user settings will not conflict with the user logging in?  

Thanks,

Yasi

---

### Post by amohanty on 2005-08-26
usermod
[http://linux.about.com/od/commands/l/blcmdl8_usermod.htm](http://linux.about.com/od/commands/l/blcmdl8_usermod.htm)

be very very careful though.

HTH
AM

---


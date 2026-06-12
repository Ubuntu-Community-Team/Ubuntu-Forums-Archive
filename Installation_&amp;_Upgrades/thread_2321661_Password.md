---
title: "Password"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by joe209 on 2016-04-23
I've just installed Ubuntu mate 16.04 on an xp pc, all went smooth. I got to the desktop to install software and it is asking me for a username and password but I haven't even created one yet?? Any help would be much appreciated!!!

---

### Post by TheFu on 2016-04-23
Installing packages requires the current userid change to root and perform the installation.  

If this is during the install of Ubuntu OS, this step will create the account that gets "sudo" access. That is important for managing the multi-user system.

If this is after the Ubuntu OS install, the account provided DURING the install is the userid/password needed.

At the core, Linux/Unix is a multi-user OS, even if you have only 1 userid.

Or am I misunderstanding the issue?

---

### Post by lisati on 2016-04-24
When you installed Ubuntu, you will have been asked for a username and password. Use this to login to your desktop. 

In order to install software, it is normal for the installation process to ask for your password, but I would be surprised if you were asked for a username as well.

For more information  on the "root" privileges provided by "sudo", have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


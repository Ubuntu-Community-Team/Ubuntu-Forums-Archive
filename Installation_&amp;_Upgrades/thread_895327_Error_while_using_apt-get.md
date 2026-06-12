---
title: "Error while using apt-get"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by Sree Pratheep on 2008-08-20
Hello,

   This is my first post to the group. 
   I am having a problem while using the apt-get program. Whenever I am using the apt-get program it is always giving the following error.

> 
root@pradheep-desktop:/home/pradheep# apt-get  install konqueror
Reading package lists... Done
Building dependency tree       
Reading state information... Done
konqueror is already the newest version.
konqueror set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/../usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/../usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)


    I tried to install the lg3d-core package. I added the following line in the /etc/apt/sources.list file. 
   > deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib 

   But it failed to install properly. After that whenever I am using apt-get it is giving the above error.

   Please help me to resolve this problem.

Sree Pratheep.

---

### Post by Kevbert on 2008-08-20
Your problem is that you cannot write to directories other than Home or subdirectories without giving permissions. What you need to do is used 'sudo', so your command should be 
```
sudo apt-get install konqueror
```
You'll then be asked for your log-in password.

---

### Post by Sree Pratheep on 2008-08-20
> **Kevbert said:**
> What you need to do is used 'sudo', so your command should be 
```
sudo apt-get install konqueror
```


Thanks for your reply.

I am already running the command as a root user.

Anyway, I tried your command, still it is giving the same error

---

### Post by Archmage on 2008-08-20
> **Sree Pratheep said:**
> I tried to install the lg3d-core package. I added the following line in the /etc/apt/sources.list file. 

According to the line this is for **Debian**, while you are here in the **Ubuntu**-forum. This could lead in a disaster.

I would suggesting removing the line, "sudo aptitude update" and than "aptitude search lg3d" - there you should see what Ubuntu-package you can use.

As far as google telling me, this is for 3d effects, don't you get them via compiz already?

---

### Post by Sree Pratheep on 2008-08-20
> **Archmage said:**
>  I would suggesting removing the line, "sudo aptitude update" 

Solved...

I removed the line from the sources.list and did a aptitude update. I also removed lg3d-core package installed from the Debian repository. 

Now I am able to use the apt-get program without any problem.

Thanks.

---


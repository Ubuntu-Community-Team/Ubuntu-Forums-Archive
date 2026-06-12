---
title: "gdm problem"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by teletis on 2008-10-28
Hi everybody,

I have a problem with gdm and I really can't find any solution:

```
tele@tele-desktop:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  gdm 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up gdm (2.20.7-0ubuntu1.1) ...
chown: changing ownership of `/var/lib/gdm/.cookie': Operation not permitted
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gdm (2.20.7-0ubuntu1.1) ...
chown: changing ownership of `/var/lib/gdm/.cookie': Operation not permitted
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
tele@tele-desktop:~$ 
```

I also get this error everytime I upgrade with the 'Update Manager'. Can anyone help?

Regards
MNH

---

### Post by cariboo on 2008-10-28
Use the Synapitc Package Manager broken package filter to correct the problem.

System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

Jim

---

### Post by teletis on 2008-10-31
Hi,

your suggestion didn't work I still have the problem. I'll try upgrading to the new ubuntu.

---

### Post by teletis on 2008-11-01
updating to the new ubuntu didn't help. Actually it just made some of the installations fail during the upgrade.

But I don't understand why I'm not able to do anything with the file: /var/lib/gdm/.cookie
I can't removed or rename it... even when I'm root.

---

### Post by teletis on 2008-11-01
It looks like I solved the problem.

First I tried booting from a live cd and then tried to remove the .cookie file but it still told me that I didn't had the rights to do that. Then I booted into my windows and mounted the linux drive in windows. With this method I was able to delete the file without any problems. 

I have booted back into ubuntu and the problem seems to be gone! :)

---


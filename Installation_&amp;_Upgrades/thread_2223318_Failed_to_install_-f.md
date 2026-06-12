---
title: "Failed to install -f"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by jusufd on 2014-05-10
Dear All,

I am having an error when I do sudo apt-get install -f. Could you please help. THANKS IN ADVANCE.

Here is the output I got:

Setting up linux-image-3.2.0-43-generic (3.2.0-43.68) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-43-generic)
dpkg: error processing linux-image-3.2.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-41-generic; however:
  Package linux-image-3.2.0-41-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.41.49); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.41.49); however:
  Version of linux-headers-server on system is 3.2.0.61.72.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
          Errors were encountered while processing:
 linux-image-3.2.0-43-generic
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kc1di on 2014-05-10
try the following command in a terminal:
```
sudo dpkg --configure -a
``` 
see if that clears it. that's pretty old kernel your trying to install is this on 12.04?

---

### Post by jusufd on 2014-05-10
I just did another command which is 
apt-get purge linux-image-3.2.0-43-generic and I got the result like this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-3.2.0-41-generic but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.41.49) but 3.2.0.61.72 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Please HELP THANKS.

---

### Post by jusufd on 2014-05-10
Hi  kc1di

I got this one:
Setting up linux-image-3.2.0-43-generic (3.2.0-43.68) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-43-generic)
dpkg: error processing linux-image-3.2.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-41-generic; however:
  Package linux-image-3.2.0-41-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.41.49); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.41.49); however:
  Version of linux-headers-server on system is 3.2.0.61.72.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-43-generic
 linux-image-server
 linux-server

THANKS.

---

### Post by kc1di on 2014-05-10
try this then ```
 sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update
```

If that works without returning errors.  Then apt-get should be clear. 

The problem seems to be that there are dependecies to that kernel that are not in the repositories at this time. 
like I said that's a pretty old kernel your trying to install.  Which kernel is now running on your system? What version is this?
type the following and list the output here. 
```
 uname -r 
```

---

### Post by jusufd on 2014-05-10
> uname -r
3.2.0-61-generic

BTW, 
>apt-get clean && sudo apt-get autoclean && sudo apt-get update 
didn't return error.

Thank You.

---

### Post by kc1di on 2014-05-10
Ok you already have a newer kernel than the one your trying to install.  so it would be a downgrade.  

you should be all set now.. if you want to upgrade do ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jusufd on 2014-05-10
But I am still don't get it when I did "sudo dpkg --configure -a" after I did "apt-get clean && sudo apt-get autoclean && sudo apt-get update" 
I am still getting an error the same error. Should I do the upgrade first? Thank You.

---

### Post by kc1di on 2014-05-10
try this ```
sudo apt-get dist-upgrade
```
then reboot and try dkpg -- configure -a again.

---

### Post by jusufd on 2014-05-10
Thank You kc1di! 
I am appreciate your help.

---

### Post by kc1di on 2014-05-10
Your Welcome,
if the problem is solved please mark the thread solved.

---


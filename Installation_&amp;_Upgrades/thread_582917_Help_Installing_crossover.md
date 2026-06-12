---
title: "Help Installing crossover"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by lucksin on 2007-10-20
Hi ,

I brought crossover and was trying to install it.. after unpacking the package it gave me an error.

```
 sudo sh install-crossover-pro-6.2.0.sh 
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/rohit' directory does not belong to you.
Point $HOME to your home directory and try again.

```

then i tried installing it from Root. 

```
root@lucky:/home/rohit/Codeweavers Crossover Office Pro 6.2.0# sh install-crossover-pro-6.2.0.sh 
Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

The DISPLAY variable is not set.  You should either login as root or use
the command "su" with no flags, to make sure setup has an X display to use.

The setup program seems to have failed on x86/glibc-2.5
Check the system requirements at:
http://www.codeweavers.com/products/cxoffice/requirements/

```

am i doing something wrong ??

---

### Post by Zombie_1985 on 2007-10-24
Just run 'sh install-crossover-pro-6.2.0.sh' - without any root privileges.

---

### Post by Zombie_1985 on 2007-10-24
PS: Run this command in terminal when the X-Server running, not when you are in console!:)

---


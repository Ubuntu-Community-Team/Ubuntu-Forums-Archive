---
title: "Locked Out of Synaptic, Sudo on 8.04"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2008-05-03
I have a new install of Hardy Heron.  I needed to install vsftpd, so I tried the easy way by following the instructions in the [Ubuntu Server Documentation.]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html") 

My command was: sudo apt-get install vsftpd

The response I got was  **sudo: unable to resolve host dave-desktop**

OK, I figured I'd try Synaptic.  But from the System menu, the application starts to load, but then drops out with no response at all after about 10 seconds.

Looks like there's something in my setup that's hosed, but what?

And yes, I DO have administrator privileges, I'm the only user.

---

### Post by Pumalite on 2008-05-03
Try editing /etc/hosts
[http://ubuntuforums.org/showthread.php?t=780209](http://ubuntuforums.org/showthread.php?t=780209)

---

### Post by bobnutfield on 2008-05-03
/etc/hosts and /etc/hostname must match.  In /etc/hosts

127.0.0.1 dave-desktop

In hostname

dave-desktop

Hope this helps

Bob

---

### Post by prshah on 2008-05-03
> **llanitedave said:**
> 
The response I got was  **sudo: unable to resolve host dave-desktop**


> **bobnutfield said:**
> /etc/hosts and /etc/hostname must match.  In /etc/hosts

127.0.0.1 dave-desktop

In hostname
dave-desktop


As bob suggested, you have to edit /etc/hosts and make sure that 127.0.0.1 is linked to your hostname. But to edit the /etc/hosts file, you need to use sudo; you can get around this catch 22 situation by either rebooting to recovery mode, or opening a terminal and typing only ```
gksudo
```, which will give you a window asking you which command to run, and as what user. Give the command as ```
gedit /etc/hosts
``` and the user as "root". Once edited and saved, sudo will start working immediately. No need for a reboot.

---

### Post by llanitedave on 2008-05-03
Thanks so much, guys!  That WAS the problem, and it's working great now!  Got vsftpd installed with no problems!  (Not configured yet).
I had to boot in rescue mode and use vim to edit /etc/hosts.  The gksudo trick got me to the window as prshah stated, but when I entered the command, the program began loading and then dropped out.  

Anyway, a good learning experience.  Thanks again!

---


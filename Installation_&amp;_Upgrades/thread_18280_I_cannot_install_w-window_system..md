---
title: "I cannot install w-window system."
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by alunar on 2005-03-05
I got a laptop IBM TP IQA103WW, so I'm trying to install Linux. I haven't installed any linux before except for installing Redhat Linux. And I got a problem now. I don't know what is wrong, so I'll explain what happens.

first, the laptop is good enough for windows, but after installing the first step of ubuntu, the computer is frozen whenever I try to install x-window-system-core. (I guess I also don't know how to use Aptitute very well.)

then, I reboot it, and it just ask me Id and password. So I type, "apt-get install x-window-system-core" then, it says,

>   dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem  

 After typing "dpkg --confiugure -a" it says again, 

 >  dpkg: unable to access dpkg status area: Read-only file system  

then, I'm stuck. I have no idea what to do. I've tried more than 8 times, and I always get the same problems.

does anybody have the solution for this problem?

---

### Post by scott_b on 2005-03-20
I am having a similar problem installing x-window-system-core. This is what I get when trying to install.

> 
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard
E: Sub-process /usr/bin/dpkg returned an error code (1)


I upgraded from warty earlier this week, and I too have a thinkpad (r40).
I'm also stuck.

---

### Post by Buffalo Soldier on 2005-03-20
Try ```
sudo apt-get install x-window-system-core
```or```
sudo dpkg --confiugure -a
```It will then ask for your password. Just type in the password that you use with your username.

---

### Post by scott_b on 2005-03-21
here's the results: 

> 
swb@cha:~ $ sudo apt-get install x-window-system-core
Reading Package Lists... Done
Building Dependency Tree... Done
x-window-system-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard
E: Sub-process /usr/bin/dpkg returned an error code (1)
> swb@cha:~ $ sudo dpkg --configure -a
Setting up gtkboard (0.11pre0-3) ...
error in control file: `Format' value not specified at /usr/sbin/install-docs line 715, <IN> line 17.
dpkg: error processing gtkboard (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 gtkboard

---


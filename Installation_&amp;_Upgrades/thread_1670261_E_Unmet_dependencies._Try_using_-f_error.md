---
title: "E: Unmet dependencies. Try using -f error?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by tripz0r on 2011-01-18
Hello,  

I was use Synaptic Package Manager to install some backtrack tools on my Ubuntu. 
I have latest updated version .  

And i got some errors while i use to installing all of that tools.  Now in my bar there is one red sign where write this:  
```
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.The error message was: 'Error: BrokenCount > 0'This is usually means that your installed package have unmet dependencies
```

When i click on that i got Update Manager, and there is checked "Libssh2-1 (New Install) Description: SSH2 client-side library (size: 108 KB)" When i click on install updates that finish but still stay there...  

I go in terminal, and write "apt-get install" then i got this :  

```
root@tripz0r-Laptop:/home/tripz0r# apt-get install Reading package lists... Done Building dependency tree       Reading state information... Done You might want to run `apt-get -f install' to correct these. The following packages have unmet dependencies:   medusa: Depends: libssh2-1 but it is not installed E: Unmet dependencies. Try using -f.
```

And i can't open Synaptic Package Manager, and i can't go in my root user, when i logout from my user to log in root, i log in and then I get a background, without icons, bars and the cursor that loads.And can't do anything ...  

Can some one help me .  

Thanks!

---

### Post by dabl on 2011-01-18
> **tripz0r said:**
> 

I go in terminal, and write "apt-get install" then i got this :  

```
root@tripz0r-Laptop:/home/tripz0r# apt-get install Reading package lists... Done Building dependency tree       Reading state information... Done You might want to run `apt-get -f install' to correct these. The following packages have unmet dependencies:   medusa: Depends: libssh2-1 but it is not installed E: Unmet dependencies. Try using -f.
```



Where did you find Ubuntu guidance to use root, and to run root commands at your user's home directory?  Honestly, that is an excellent way to bork your system beyond recovery -- you may be looking at a reinstallation.  :cry:

So, exit the root prompt.

Now, if apt is not yet destroyed, you might be able to run

```
sudo dpkg --configure -a
```

Does it run to completion?  If so, try

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get autoremove
```

Let's see where that puts you.

---

### Post by tripz0r on 2011-01-18
Hey,

Thanks for your replay!

When i use this command 
sudo dpkg --configure -a 
i got this :

```
tripz0r@tripz0r-Laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of medusa:
 medusa depends on libssh2-1; however:
  Package libssh2-1 is not installed.
dpkg: error processing medusa (--configure):
 dependency problems - leaving unconfigured
Setting up lynx (2.8.6-2.1ubuntu3) ...
update-alternatives: error: alternative path /usr/bin/lynx doesn't exist.
dpkg: error processing lynx (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up autoscan (1.50-bt0) ...
ln: creating symbolic link `/usr/bin/nautilus': File exists
dpkg: error processing autoscan (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up nvidia-driver (256.40-bt1) ...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
FATAL: Module nvidia not found.
dpkg: error processing nvidia-driver (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of medusa-menu:
 medusa-menu depends on medusa; however:
  Package medusa is not configured yet.
dpkg: error processing medusa-menu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lynx-menu:
 lynx-menu depends on lynx; however:
  Package lynx is not configured yet.
dpkg: error processing lynx-menu (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 medusa
 lynx
 autoscan
 nvidia-driver
 medusa-menu
 lynx-menu

```


And when i use this:


```
tripz0r@tripz0r-Laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  medusa: Depends: libssh2-1 but it is not installed
E: Unmet dependencies. Try using -f.

```


hmm...i think i broke my OS? :/ did I?

---

### Post by mandzo84 on 2011-01-18
have you added any non-standard repositories (through Synaptic, or by editing /etc/apt/sources.list)?

---

### Post by mandzo84 on 2011-01-18
have you added any non-standard repositories (through Synaptic, or by editing /etc/apt/sources.list)?

---

### Post by tripz0r on 2011-01-19
I only changed by root this  "/etc/xdg/menus/applications.menu"

btw. when i gedit /etc/apt/sources.list i got in editor just this:

```
deb http://archive.offensive-security.com pwnsauce main microverse macroverse restricted universe multiverse
```

---

### Post by mandzo84 on 2011-01-19
You need to have only Ubuntu sources. The most easiest way to brake your system is to add some non-trusted untested sources.

You can edit this with:
```
sudo software-properties-gtk
```
Or by editing manually. Here is a useful generator if you have problems: [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

Then try this:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
```

---

### Post by tripz0r on 2011-01-19
```
tripz0r@tripz0r-Laptop:~$ sudo software-properties-gtk
[sudo] password for tripz0r: 
sh: kde-config: not found
sh: kde-config: not found
Segmentation fault

```

This doesn't work, like i see...

I will try other manual method, but i am not really expert...There is not all clear for me, i will try to do that .
If you want you can add me on msn : [email]ffstrip@hotmail.com[/email] :)

Thanks

---


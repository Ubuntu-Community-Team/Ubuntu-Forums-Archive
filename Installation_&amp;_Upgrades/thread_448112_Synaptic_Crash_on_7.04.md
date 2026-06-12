---
title: "Synaptic Crash on 7.04"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Coolit on 2007-05-18
Hi,

I've just upgraded my laptop to 7.04 but I have an issue with Synaptic, It appears  for a few seconds then crashes just as it finishes loading, heres the console error:-

> coolit@coolit-laptop:~$ sudo synaptic

(synaptic:8429): XML-CRITICAL **: Document is empty


(synaptic:8429): XML-CRITICAL **: Start tag expected, '<' not found


(synaptic:8429): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed

(synaptic:8429): libglade-WARNING **: did not finish in PARSER_FINISH state
synaptic: rguserdialog.cc:223: bool RGGladeUserDialog::init(const char*): Assertion `gladeXML' failed.
Aborted (core dumped)
coolit@coolit-laptop:~$ 



Hope someones able to shed some light on this, thanks for the help in advance:)

---

### Post by taurus on 2007-05-18
Try

```
**gksudo** synaptic
```

---

### Post by Coolit on 2007-05-19
Thanks for the reply,

gksudo gives the same error.

---

### Post by taurus on 2007-05-19
What about

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  Are you running Breezy or Dapper?

---

### Post by Coolit on 2007-05-19
Sorry my signature was misleading, its not been updated in a while so I've edited it.

It's a fresh install of Feisty that I'm using, just installed it on Thursday, its fully up to date.

---

### Post by taurus on 2007-05-19
What happens when you run those two commands from a terminal?  Is that a x86 or a x86_64 verison of Feisty?

---

### Post by Coolit on 2007-05-19
Its an x86 Centrino Mobile laptop with 32bit Feisty installed. Apt-get works perfectly from the CMD line as does the Add/Remove function in the main menu, heres the console output as requested:-

> coolit@coolit-laptop:~$ sudo aptitude update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]         
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release [38.4kB]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages [14B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages [4073B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages [1751B]
Fetched 51.2kB in 0s (62.0kB/s)
Reading package lists... Done
coolit@coolit-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by taurus on 2007-05-19
Let's see if you can run anything else as root.

```
gksudo nautilus
```

---

### Post by Coolit on 2007-05-19
That works fine,

The first time I ran nautilus from the CMD line I received the following console output:-

> coolit@coolit-laptop:~$ gksudo nautilus
(nautilus:9138): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension


It did run fine though with the above error.


I closed it and there was no error 2nd time round
> coolit@coolit-laptop:~$ gksudo nautilus
Initializing gnome-mount extension
coolit@coolit-laptop:~$ 

---

### Post by taurus on 2007-05-19
That message is just a warning.  

Why don't you reboot and then run this command again to see what happens.

```
gksudo synaptic
```

---

### Post by Coolit on 2007-05-19
Its the same unfortunatly

---

### Post by Coolit on 2007-05-21
Finally fixed the problem:)

I just removed the synaptic .deb and its dependencies with apt then did a re-install and its working great now.

Thanks for the help Taurus :)

---


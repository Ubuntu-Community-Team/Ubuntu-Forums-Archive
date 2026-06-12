---
title: "moblock completely broken"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Dawa on 2008-02-17
hey all.  After upgrading to the latest version of moblock; it stopped working completely.  i tried to uninstall it but i keep getting error messages.  now the /etc/moblock/ directory is gone, but synaptic still thinks moblock is installed and will not let me remove it or re-install it.

HELP!!!

---

### Post by PmDematagoda on 2008-02-17
Post the output of:-
```
sudo apt-get install -f
```

---

### Post by Dawa on 2008-02-17
Here's what I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflash0c2 airstrike-common libgnorbagtk0 libggi2 libaudacious5 libgii1
  libgii1-target-x imlib-base libgeoip1 liborbit0 gdk-imlib11 libqt3-mt
  libjsw2 libswt3.2-gtk-jni scummvm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up moblock (0.9~rc2-1+gutsy+i386) ...
Can't load configuration from /etc/moblock/moblock.conf, exiting.
dpkg: error processing moblock (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Dawa on 2008-02-17
okay I managed to rip it out manually by following the "dangerous, not recommended" suggestion in this thread:  [http://ubuntuforums.org/archive/index.php/t-160331.html](http://ubuntuforums.org/archive/index.php/t-160331.html)

however, after trying to do a fresh install the same thing happens.  there is some kind of error, moblock is broken, and it won't let me remove it.  here is what synaptic tells me when i try to remove:

[IMG]http://i51.photobucket.com/albums/f375/Dawa73/moblock.jpg[/IMG]

edit:  I installed leafpad to just to make sure that I didn't break synaptic.

---

### Post by delgiu on 2008-02-17
Hi, I've upgraded moblock and I have the same problem. When I try to start moblock I get:
/usr/bin/moblock-control: 620: Syntax error: Bad substitution

hope someone can help...

---

### Post by empthollow on 2008-02-17
sounds like there may be a problem with the moblock package.  If that is the case you should post in this thread, the developer of moblock posts here. [http://ubuntuforums.org/showthread.php?t=192559&page=110](http://ubuntuforums.org/showthread.php?t=192559&page=110)

---

### Post by jre on 2008-02-17
Hey, I'm the developer, so: Sorry for any inconvenience.
I'm just releasing a fixed version.
You can also fix it maually:
Change the first line of /usr/bin/moblock-control to:
```
#!/bin/bash
```

---

### Post by edonnelly on 2008-02-17
Your fix worked perfectly! Thanks!

---

### Post by Dandys on 2008-02-17
> **jre said:**
> ..I'm just releasing a fixed version.
I installed moblock from repository now again and still is broken, but your fix help me and moblock seems is running good.
Only when I checked moblock status I got this:
$ sudo dpkg -s moblock
Package: moblock
Status: install ok half-configured

after this command it was all right:
$ sudo dpkg --configure -a

$ sudo dpkg -s moblock
Package: moblock
Status: install ok installed

Thank you for your advice jre!

---

### Post by Dawa on 2008-02-17
Dandys, did you update the packages list?  hit the "Reload" button in synaptic or do a:

```
sudo apt-get update
```

I almost re-installed the broken version myself.  haha.

---

### Post by Dandys on 2008-02-18
> **Dawa said:**
> Dandys, did you update the packages list?  hit the "Reload" button in synaptic or do a:

```
sudo apt-get update
```

I almost re-installed the broken version myself.  haha.
No I didn't reload my adept but adept updater offered me now a new version of moblock and this update work good. Thanks jre!

---


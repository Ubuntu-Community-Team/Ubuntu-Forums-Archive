---
title: "I face with a problem in Package"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by sinaphysics on 2012-11-27
When I install a new app or update my system I see this problem. I use Ubuntu 12.10 with gnome shell.  :sad:

```

installArchives() failed: Selecting previously unselected package libsexy2. 
(Reading  database ...  (Reading database ... 5% (Reading database ...  10% (Reading database ... 15% (Reading database ... 20% (Reading  database ... 25% (Reading database ... 30% (Reading database ...  35% (Reading database ... 40% (Reading database ... 45% (Reading  database ... 50% (Reading database ... 55% (Reading database ...  60% (Reading database ... 65% (Reading database ... 70% (Reading  database ... 75% (Reading database ... 80% (Reading database ...  85% (Reading database ... 90% (Reading database ... 95% (Reading  database ... 100% (Reading database ... 197414 files and directories  currently installed.) 
Unpacking libsexy2 (from .../libsexy2_0.1.11-2build3_i386.deb) ... 
Selecting previously unselected package xchat-common. 
Unpacking xchat-common (from .../xchat-common_2.8.8-3ubuntu15_all.deb) ... 
Selecting previously unselected package xchat. 
Unpacking xchat (from .../xchat_2.8.8-3ubuntu15_i386.deb) ... 
Selecting previously unselected package xchat-indicator. 
Unpacking xchat-indicator (from .../xchat-indicator_0.3.11-0ubuntu4_i386.deb) ... 
Processing triggers for gconf2 ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
dpkg: error processing libsdl-image1.2:i386 (--configure): 
 package libsdl-image1.2:i386 is not ready for configuration 
 cannot configure (current status `half-installed') 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on libsdl-image1.2 (>= 1.2.10); however: 
  Package libsdl-image1.2:i386 is not installed. 
 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up libsexy2 (0.1.11-2build3) ... 
Setting up xchat-common (2.8.8-3ubuntu15) ... 
Setting up xchat (2.8.8-3ubuntu15) ... 
Setting up xchat-indicator (0.3.11-0ubuntu4) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 libsdl-image1.2:i386 
 vlc 
Error in function:  
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on libsdl-image1.2 (>= 1.2.10); however: 
  Package libsdl-image1.2:i386 is not installed. 
 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 


```

---

### Post by NikTh on 2012-11-27
Hi , 

have you tried to install the package that missing ? 

```
sudo apt-get install libsdl-image1.2:i386
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get dist-upgrade
```

Thanks

---

### Post by sinaphysics on 2012-11-27
When I do first command line
> sudo apt-get install libsdl-image1.2:i386

the result is 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl-image1.2 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0 B/31.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libsdl-image1.2:i386 (--configure):
 package libsdl-image1.2:i386 is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libsdl-image1.2 (>= 1.2.10); however:
  Package libsdl-image1.2:i386 is not installed.

dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libsdl-image1.2:i386
 vlc
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by NikTh on 2012-11-27
If you remove vlc ? 
```
sudo apt-get remove --purge vlc 
sudo apt-get install -f 
sudo dpkg --configure -a
``` 

Also remove the unwanted packages with this command
```
sudo apt-get --purge autoremove
```

Thanks

---

### Post by sinaphysics on 2012-11-27
No I don't remove VLC. Against I want it cos I use it very much. I see this problem when I want to install new app or update my system. Totally I have no problem in my system operation but I feel some unsettling about this matter.

---

### Post by NikTh on 2012-11-27
> **sinaphysics said:**
> No I don't remove VLC. Against I want it cos I use it very much.
I did not mean to throw away Vlc. I know is good program and I use it too. But maybe if you purge vlc and execute above commands the problem resolved. Then you can install again Vlc. 
> **sinaphysics said:**
>  I see this problem when I want to install new app or update my system.  Are you able or not to install a new app ? If you're unable then the system not working as it should and we must correct it. 

Thanks

---

### Post by sinaphysics on 2012-11-28
When I do 
```
sudo apt-get remove --purge vlc
```the result is same :(
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'vlc' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0 B/31.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libsdl-image1.2
Install these packages without verification [y/N]? y
dpkg: error processing libsdl-image1.2:i386 (--configure):
 package libsdl-image1.2:i386 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libsdl-image1.2:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And in addition I have no problem in installing new apps just in end of each installation I see this error. I think this error backs to my gnome shell because previously which I was using Unity I never see this error.

---

### Post by NikTh on 2012-11-28
Lets take more drastic measures. 

Execute bellow commands with order
```
wget "http://ubuntuone.com/16urbk8yYDSe1SDhIM18sa" -O ~/fixpackage
chmod +x fixpackage
sudo ./fixpackage
```The script fixpackage is not something special , it just includes the commands from here [Step 5]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure")
You can examine the scrip **before** running the "sudo" command , with gedit editor 
```
gedit fixpackage
```Thanks

---


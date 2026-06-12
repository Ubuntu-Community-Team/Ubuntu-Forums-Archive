---
title: "Sun-Java6-jdk bad install"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Boomerkuwanger on 2010-02-01
Hello all I was trying to install the sun jdk to use javac.

I installed using this:

```
sudo apt-get install sun-java6-jdk
```

Unfortunatly i made the error of quitting out of the terminal during the licensing information because it seemed stuck, which apparently screws it up.

So pretty much i've tried everything on this thread [http://ubuntuforums.org/showthread.php?t=1369721](http://ubuntuforums.org/showthread.php?t=1369721) and a few others including:

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update
```

Then tried to reinstall and recieved this message:

```
$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jdk sun-java6-jre
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/54.0MB of archives.
After this operation, 159MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 186498 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-15-1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6-15-1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
 /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb
 /var/cache/apt/archives/sun-java6-jdk_6-15-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please let me know what I can do! 

Thanks boomer

---

### Post by oldos2er on 2010-02-01
If you have any other package manager open, e.g. Synaptic, Update Manager, or Ubuntu Software Center, make sure they're closed. Try ```
sudo apt-get clean && sudo apt-get update && sudo apt-get install sun-java6-jdk
```

If this doesn't work, please post the terminal output again.

Btw, to accept Sun's java license, hit Tab to highlight Ok, then hit Enter.

---

### Post by Boomerkuwanger on 2010-02-02
This is what I get after putting in the code. 

```
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/main Translation-en_US                         
Get:2 http://dl.google.com stable Release [2,540B]                             
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Get:3 http://dl.google.com stable/main Packages [905B]                         
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://packages.medibuntu.org karmic Release                     
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Hit http://security.ubuntu.com karmic-security/main Packages         
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://us.archive.ubuntu.com karmic Release
Get:5 http://us.archive.ubuntu.com karmic-updates Release [44.1kB]             
Hit http://security.ubuntu.com karmic-security/restricted Packages        
Hit http://security.ubuntu.com karmic-security/multiverse Packages         
Hit http://security.ubuntu.com karmic-security/universe Packages           
Hit http://packages.medibuntu.org karmic/non-free Packages                 
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/universe Packages
Get:6 http://us.archive.ubuntu.com karmic-updates/main Packages [160kB]
Get:7 http://us.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Get:8 http://us.archive.ubuntu.com karmic-updates/multiverse Packages [6,942B]
Get:9 http://us.archive.ubuntu.com karmic-updates/universe Packages [97.6kB]
Fetched 312kB in 2s (120kB/s)                         
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source sun-java6-plugin
  ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jdk sun-java6-jre
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.0MB of archives.
After this operation, 159MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/multiverse sun-java6-jre 6-15-1 [6,421kB]
Get:2 http://us.archive.ubuntu.com karmic/multiverse sun-java6-bin 6-15-1 [29.1MB]
Get:3 http://us.archive.ubuntu.com karmic/multiverse sun-java6-jdk 6-15-1 [18.5MB]
Fetched 54.0MB in 3min 25s (263kB/s)                                           
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 187912 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-15-1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6-15-1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
 /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb
 /var/cache/apt/archives/sun-java6-jdk_6-15-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by oldos2er on 2010-02-02
Did you run sudo apt-get clean first?

---

### Post by Boomerkuwanger on 2010-02-02
I ran the code you put in your first response, with the '&&' and all

---

### Post by oldos2er on 2010-02-02
Found this: [https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/495508](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/495508) and [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/349469](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/349469)
You may want to add to those bug reports. I'm afraid this one's beyond my limited ability to help. Sorry.

---


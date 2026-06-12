---
title: "I may have wrecked apt-get"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by yssida on 2010-01-01
Good day!

I tried installing java by the command:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

I made the stupid decision of closing the terminal despite warning (yes it's my fault). And now when I retyped the same command, it tells me to try 

```
sudo apt-get -f install
```

to fix a problem. However this only introduced other problems which led me to delete the /var/cache/debconf/config.dat but it only introduced me to other problems

therefore i closed the terminal and opened synaptic (I thought it would probably be easier to install from there) and found out that in addition to not finishing the installation, I have 2 broken packages resulting from that aborted install. So I tried repairing it (maybe I could then install the other packages afterwards) but it returned the following error message

```

debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 162861 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_i386.deb) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-15-1_i386.deb
 /var/cache/apt/archives/sun-java6-jre_6-15-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-15-1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-15-1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-fonts
 sun-java6-plugin


```

I hope my post was detailed enough. And I promise never to mess with the terminal while it was installing something. I hope someone could help.

Thanks!

---

### Post by Shazaam on 2010-01-01
"debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable"
"debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable"
This usually means you have Ubuntu Software Center/Update Manager/Synaptic open and are trying to run apt-get at the same time and the files are locked. Close them and run apt-get by itself in terminal.

Try these commands...
1.-
```
sudo dpkg --configure -a
```
2.-
```
sudo apt-get install -f
```
3.-
```
sudo apt-get update
```
If they complete successfully (no errors) try to install java again using your apt-get command from before.

---

### Post by mr clark25 on 2010-01-01
if it still doesn't work, you may want to try aptitude. it is used the same way as apt-get.

code:
sudo aptitude install program

or at least i think that is how you use it. someone correct me if i am wrong.

---


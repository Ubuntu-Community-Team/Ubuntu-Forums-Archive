---
title: "uBUNTU sOFTWARE cENTER"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by slixz85 on 2010-11-24
Hi thanks for checkin this post. ubuntu software center won't let me install anything anymore the install button changed from install to "use this source" and i get the following error message:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 116, in _process_transaction
    self.update_cache()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 426, in update_cache
    self._cache.update(progress, raiseOnError=True)
  File "/usr/lib/python2.6/dist-packages/apt/deprecation.py", line 103, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 309, in update
    raise LockFailedException("Failed to lock %s" % lockfile)
LockFailedException: Failed to lock /var/lib/apt/lists/lock




any help greatly appreciated

---

### Post by Zookalicious on 2010-11-24
Check your software sources Ubuntu Software Center > Edit > Software Sources > Other Software and make sure that the sources you are trying to use are checked. Then completely close the software center, open a terminal and type "sudo apt-get update".

Try installing again and see if it works. If it doesn't, try installing the package by typing "sudo apt-get install <name of package>" and see if that works any better.

---

### Post by slixz85 on 2010-11-24
when i try both methods they dont work here is screenshot of my sources and also what is says in terminal:

sudo slixz@slixz-netbook:~$ sudo apt-get install PokerTH
[sudo] password for slixz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package PokerTH
slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ sudo apt-get install PokerTH
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package PokerTH
slixz@slixz-netbook:~$

---

### Post by Zookalicious on 2010-11-24
Sources look fine. The "unable to open lock file " error often comes up when some part of the software center is still running. Close the software center and any running terminals. To be sure type the following:
```

sudo killall software-center
sudo killall apt

```

Try just running the update then. 

Also make sure you are typing the correct name of the package. PokerTH does not seem to be a real package-name. 

Just for experimentation, try installing something small like w3m (text web browser)
```

sudo apt-get install w3m

```

---

### Post by slixz85 on 2010-11-24
alright before i remove something i shouldn't with the great autoremove(haha) this seems unnormal for this many programs to be list it has said a coupe before

sslixz@slixz-netbook:~$ sudo killall software-center
[sudo] password for slixz: 
software-center: no process found
slixz@slixz-netbook:~$ sudo kill all apt
ERROR: garbage process ID "apt".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
slixz@slixz-netbook:~$ clear

slixz@slixz-netbook:~$ sudo apt-get install w3m
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w3m is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl python-pygoocanvas libqca2 gwibber-service
  libpackagekit-glib2-12 python-paramiko oxygen-icon-theme python-pycurl
  libqt4-sql-mysql kdelibs5 libindicate-gtk2 libqt4-qt3support
  libgoocanvas-common shared-desktop-ontologies libmagickcore2-extra
  libexiv2-6 nautilus-sendto-empathy python-gtkspell libpackagekit-qt-12
  libqt4-xmlpatterns libsoprano4 libpolkit-qt-1-0 libqt4-webkit python-sip
  kdelibs5-data libdbusmenu-qt2 icoutils libqt4-sql-sqlite libqt4-sql
  libqt4-svg python-packagekit libstreamanalyzer0 packagekit libplasma3
  python-egenix-mxdatetime kdelibs-bin libattica0 python-egenix-mxtools
  libstreams0 imagemagick packagekit-backend-apt exiv2 python-wnck libssh-4
  virtuoso-nepomuk soprano-daemon kdebase-runtime-data libiodbc2
  gstreamer0.10-gnonlin libgoocanvas3 empathy-common python-indicate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
slixz@slixz-netbook:~$ 

cause this thing seems wierd and i notice python in there i am newbie just thought it is important

---

### Post by Zookalicious on 2010-11-24
Did you run "sudo apt-get update" yet? The w3m installation was just supposed to be a test (although you seem to already have it installed) after you updated :P which is the whole point of killing software-center and apt.

Those will generally be small files and libraries. Its up to you if you want to get rid of them (and trust synaptics when it's telling you that they aren't needed anymore;) )

---

### Post by oldos2er on 2010-11-25
Try the command without capital letters ```
sudo apt-get install pokerth
```

---

### Post by slixz85 on 2010-11-25
yes i did use sudo apt-get update as posted above. forgot at first then did. Its just the same message i get no matter what. i open a new terminal type in sudo apt-get update then it shows:

slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ 

it does this every reboot and new session

and yeah i have tried the programs spelled differently as well also tried Marble and marble a globe program under science in software center and does the same thing.

what is the lock and list any way?

---


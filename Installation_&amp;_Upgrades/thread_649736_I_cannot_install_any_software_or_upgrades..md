---
title: "I cannot install any software or upgrades."
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by e102 on 2007-12-25
I cannot install any software or upgrades. whenever I try ,an error message stating 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
I have so far been unsuccessful in correcting this error.

---

### Post by taurus on 2007-12-25
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Don't forget to close synaptic or Add/Remove first if you have them open before you run those three commands above.

---

### Post by oldos2er on 2007-12-25
Run "sudo dpkg --configure -a"

---

### Post by e102 on 2007-12-26
I have already tried running sudo-apt get update/upgrade  in terminal but i receive the message
"E: dpkg was interrupted, you must manually  run "dpkg --configure -a" to correct the problem."
and when i run "dpkg --configure -a" i get the message " 
e102@e102-desktop:~$ sudo --configure -a
sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
which I do not understand.

---

### Post by taurus on 2007-12-26
It's

```
**sudo dpkg --configure -a**
```

---

### Post by e102 on 2007-12-26
Thank you for that. Now i have the message.

e102@e102-desktop:~$ sudo dpkg --configure -a
dpkg: error processing python-poker-network (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 python-poker-network.

And I do not recall installing "python-poker-network".When i tried removing it using synaptic package manager i received the message.

An error occured

The following details are provided:
E: python-poker-network: Package is in a very bad inconsistent state - you should

But there was no text after "you should" and the package was not removed.What should I do?

---

### Post by taurus on 2007-12-26
Try

```
sudo apt-get install -f
```

---

### Post by Bobrm2 on 2008-01-31
I have the same problem, except that I wish to install the python 2.5 poker-network; have also as seem below made several attempts to clean up and reinstall the program. Feel that if I could delete the attempts to install, I might be able to make a clean start. Unable to delete and the problem appears as I download other programs/upgrades from "Add/Remove" or Synaptic Package manager?  TIA

Bob


bob@Bob:~$ sudo dpkg --configure -a
Setting up python-poker-network (1.2.0-1ubuntu1) ...
/usr/bin/rsync --exclude CVS --delete -a -v --ignore-existing /usr/share/poker-network/conf/ /etc/poker-network/
building file list ... done

sent 115 bytes  received 20 bytes  270.00 bytes/sec
total size is 10615  speedup is 78.63
Config::checkVersion: /etc/poker-network/poker.bot.xml: up to date
Config::checkVersion: /etc/poker-network/poker.client.xml: up to date
/etc/poker-network/poker.server.xml:58: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="ISO-8859-1"?>                     <?xml version="1.0" encoding="ISO-
     ^
/etc/poker-network/poker.server.xml:58: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="ISO-8859-1"?>                     <?xml version="1.0" encoding="ISO-
                                                                     ^
/etc/poker-network/poker.server.xml:59: parser error : Extra content at the end of the document
<server xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   <server xmlns:xsi=
^
Traceback (most recent call last):
  File "/usr/sbin/pokerconfigupgrade", line 121, in <module>
    sys.exit(main())
  File "/usr/sbin/pokerconfigupgrade", line 103, in main
    config.load(file)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokernetworkconfig.py", line 46, in load
    status = pokerengineconfig.Config.load(self, path)
  File "/usr/lib/python2.5/site-packages/pokerengine/pokerengineconfig.py", line 69, in load
    self.doc = libxml2.parseFile(self.path)
  File "/var/lib/python-support/python2.5/libxml2.py", line 1280, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
libxml2.parserError: xmlParseFile() failed
dpkg: error processing python-poker-network (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-poker-network
bob@Bob:~$ 
bob@Bob:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdegames-card-data libkdegames1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-poker-network (1.2.0-1ubuntu1) ...
/usr/bin/rsync --exclude CVS --delete -a -v --ignore-existing /usr/share/poker-network/conf/ /etc/poker-network/
building file list ... done

sent 115 bytes  received 20 bytes  270.00 bytes/sec
total size is 10615  speedup is 78.63
Config::checkVersion: /etc/poker-network/poker.bot.xml: up to date
Config::checkVersion: /etc/poker-network/poker.client.xml: up to date
/etc/poker-network/poker.server.xml:58: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="ISO-8859-1"?>                     <?xml version="1.0" encoding="ISO-
     ^
/etc/poker-network/poker.server.xml:58: parser error : XML declaration allowed only at the start of the document
<?xml version="1.0" encoding="ISO-8859-1"?>                     <?xml version="1.0" encoding="ISO-
                                                                     ^
/etc/poker-network/poker.server.xml:59: parser error : Extra content at the end of the document
<server xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   <server xmlns:xsi=
^
Traceback (most recent call last):
  File "/usr/sbin/pokerconfigupgrade", line 121, in <module>
    sys.exit(main())
  File "/usr/sbin/pokerconfigupgrade", line 103, in main
    config.load(file)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokernetworkconfig.py", line 46, in load
    status = pokerengineconfig.Config.load(self, path)
  File "/usr/lib/python2.5/site-packages/pokerengine/pokerengineconfig.py", line 69, in load
    self.doc = libxml2.parseFile(self.path)
  File "/var/lib/python-support/python2.5/libxml2.py", line 1280, in parseFile
    if ret is None:raise parserError('xmlParseFile() failed')
libxml2.parserError: xmlParseFile() failed
dpkg: error processing python-poker-network (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-poker-network
E: Sub-process /usr/bin/dpkg returned an error code (1)
bob@Bob:~$

---


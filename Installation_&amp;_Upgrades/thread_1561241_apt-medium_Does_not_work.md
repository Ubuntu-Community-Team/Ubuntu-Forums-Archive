---
title: "apt-medium Does not work"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by Pev on 2010-08-26
I'm moving a bunch of server machines on to a new linux distro. I've chosen Ubuntu because it seems to have the best support and so far everything been working great. But I've hit my first major snag.

I cannot have these servers connected to the internet so I need to keep them updated offline. After going through [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline) I've decided that [apt-medium]("http://wiki.debian.org/AptMedium") is the best solution to my problem. However I cannot get it working. I'm using a fully updated version 10.04 desktop amd64 to test the program. After running
```
sudo ./apt-medium-download apt-get -s install python-scipy
```I get:
```
E: Couldn't find package python-scipy
```If I do:
```
sudo ./apt-medium-download apt-get -s install python
```I get a huge list of dependences which are not installable.

I have already run
```
sudo ./apt-medium-init 
```I'm guessing apt-medium is using an old repository for some silly reason. But I cannot see where it's going wrong. I mean it takes the apt-get command in from the command line so you think this shouldn't be an issue.

Anyway if anyone has got this working for version 10.04 I would love to here from them. Note the servers do not have a GUI (gnome/KDE) installed so I cannot use [SynapticPackageDownloadScript]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript?action=show&redirect=SynapticPackageDownloadScript") unfortunately because this does seem to work.

As a last resort I'll try and right a script file but I'm hopping someone else has done this for me.

---


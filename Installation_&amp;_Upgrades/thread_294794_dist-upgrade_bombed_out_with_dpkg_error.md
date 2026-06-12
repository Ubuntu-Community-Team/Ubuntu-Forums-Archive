---
title: "dist-upgrade bombed out with dpkg error"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by parsival on 2006-11-07
Hi Forum,

 sudo apt-get dist-upgrade (from 5.10 to 6.06)
bombed out with the error
Errors were encountered while processing:
 nis
E: Sub-process /usr/bin/dpkg returned an error code (1)

Most things seem to work -- but I cant install anthing as I get the same error (see below). I dont think I am even running nis 

commands like 
  sudo apt-get --force-yes  install nis
run into the same error

sudo apt-get  install libtunepimp2c2a
Reading package lists... Done
Building dependency tree... Done
libtunepimp2c2a is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nis (3.15-3ubuntu2) ...
chmod: cannot access `nis': No such file or directory
dpkg: error processing nis (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nis
E: Sub-process /usr/bin/dpkg returned an error code (1)


Bye

---

### Post by parsival on 2006-11-08
OK -- I have fixed it!

The problem is probably caused by the fact that I started dist-upgrading while not having commented out non-official
Ubuntu repositories!! So here is  how I fixed it

sudo mv sources.list.clean sources.list
sudo apt-get update
#Let's now try to configure all packages #that are unconfigured :
sudo dpkg --configure -a
#no output and problem is still there, so
sudo aptitude remove -f nis
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  libimlib2
The following packages will be REMOVED:
  nis
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 803kB will be freed.
Writing extended state information... Done
(Reading database ... 187677 files and directories currently installed.)
Removing nis ...
/var/lib/dpkg/info/nis.prerm: line 10: /etc/init.d/nis: 
No such file or directory
dpkg: error processing nis (--remove):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: unknown initscript, /etc/init.d/nis not found.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 100
Errors were encountered while processing:
 nis
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

#so it cant find /etc/init.d/nis 
cd init.d/
ls nis*
nis.backup*  nis.dpkg-dist*

#what is going on here? Perhaps a process #didnt finish
sudo cp nis.backup nis
#now I have a /etc/init.d/nis file -- lets 
#remove it and reinstalled it
sudo aptitude remove -f nis  
sudo apt-get install nis
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nis
.
.
Setting up nis (3.15-3ubuntu2) ...
Setting NIS domainname to: ******
Starting NIS services: ypbind [binding to YP server .......... backgrounded]


#now apt-get installs work!!
# but now I have nis installed and I get 
#YPBINDPROC_DOMAIN: Domain not bound
#messages all the time
sudo /etc/init.d/nis stop
#will stop nis but how do I turn it off all 
#the time.
#There is no /sbin/chkconfig utility in #ubuntu,
#so I just removed all the symbolic links #from the
#/etc/rc?.d/ directories
rm   /etc/rc?.d/*nis*

All fixed and a happy ending!

Bye

---


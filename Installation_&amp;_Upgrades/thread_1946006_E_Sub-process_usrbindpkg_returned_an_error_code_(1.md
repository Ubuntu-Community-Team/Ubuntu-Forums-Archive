---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by herojeett on 2012-03-24
Hello All,
I am new to ubuntu and I am trying to set-up a network with my windows XP machine. I followed the instruction for installing and configuring SAMBA, but not successfully :(. 

I am getting the following error 
sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 linux-headers-3.0.0-12 esound-common libesd0
  linux-headers-3.0.0-12-generic libaudiofile0 wine1.2-gecko
  flashplugin-downloader
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ...
Administrator password will be set randomly!
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
    
When I tried to remove the installation also, I am getting the same error
:~$ sudo apt-get purge samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 linux-headers-3.0.0-12 esound-common libesd0
  linux-headers-3.0.0-12-generic libaudiofile0 wine1.2-gecko
  flashplugin-downloader
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 23.0 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 222421 files and directories currently installed.)
Removing samba ...
nmbd stop/waiting
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ...
Administrator password will be set randomly!
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help

---

### Post by Rubi1200 on 2012-03-24
Hi,

run the following commands and post any errors reported:

```
sudo apt-get clean
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by rpangelov on 2012-11-08
or maybe try to clean /var/dpkg/lib/info like that:

> sudo su
cd /var/dpkg/lib/info/
ls -l
rm -rf [name of the package which causes the problems]*

I had familiar problem with usplash-smooth and I soved it by:

> rm -rf /var/dpkg/lib/info/usplash-smooth*

---


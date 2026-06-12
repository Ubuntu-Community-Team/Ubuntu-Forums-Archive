---
title: "Remove PPA"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by doctortonic on 2011-04-15
```
wolfy@Stardust:~$ sudo apt-get install python-gdm2setup
[sudo] password for wolfy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gdm2setup
wolfy@Stardust:~$ sudo add-apt-repository ppa:gdm2setup/gdm2setup
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 33E1C2F5E880004C06B6696B1780999033C3C104
gpg: requesting key 33C3C104 from hkp server keyserver.ubuntu.com
gpg: key 33C3C104: public key "Launchpad GDM2Setup" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
wolfy@Stardust:~$ sudo apt-get update
Hit http://ro.archive.ubuntu.com maverick Release.gpg
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://ro.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://ro.archive.ubuntu.com maverick Release                    
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ro.archive.ubuntu.com maverick-updates Release                      
Get:2 http://security.ubuntu.com maverick-security Release [31.4kB]            
Ign http://ppa.launchpad.net maverick/main Sources                   
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ro.archive.ubuntu.com maverick/main Sources                         
Ign http://ppa.launchpad.net maverick/main i386 Packages                     
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://ro.archive.ubuntu.com maverick/restricted Sources                   
Ign http://ppa.launchpad.net maverick/main Sources                           
Hit http://ro.archive.ubuntu.com maverick/universe Sources                     
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ro.archive.ubuntu.com maverick/multiverse Sources
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Hit http://ro.archive.ubuntu.com maverick/main i386 Packages                   
Get:3 http://security.ubuntu.com maverick-security/main Sources [37.3kB]
Hit http://ro.archive.ubuntu.com maverick/restricted i386 Packages           
Err http://ppa.launchpad.net maverick/main i386 Packages                     
  404  Not Found
Hit http://ro.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://ro.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://ro.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://ro.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://ro.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://ro.archive.ubuntu.com maverick-updates/multiverse Sources           
Get:4 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:5 http://security.ubuntu.com maverick-security/universe Sources [13.8kB]
Hit http://ro.archive.ubuntu.com maverick-updates/main i386 Packages        
Get:6 http://security.ubuntu.com maverick-security/multiverse Sources [1,756B] 
Get:7 http://security.ubuntu.com maverick-security/main i386 Packages [132kB]
Hit http://ro.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://ro.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://ro.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Get:8 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:9 http://security.ubuntu.com maverick-security/universe i386 Packages [56.6kB]
Get:10 http://security.ubuntu.com maverick-security/multiverse i386 Packages [3,737B]
Fetched 277kB in 2s (136kB/s)                          
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
wolfy@Stardust:~$ sudo apt-get install python-gdm2setup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gdm2setup
wolfy@Stardust:~$ sudo add-apt-repository ppa:gdm2setup/gdm2setup
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 33E1C2F5E880004C06B6696B1780999033C3C104
gpg: requesting key 33C3C104 from hkp server keyserver.ubuntu.com
gpg: key 33C3C104: "Launchpad GDM2Setup" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
wolfy@Stardust:~$ sudo remove-apt-repository ppa:gdm2setup/gdm2setup
sudo: remove-apt-repository: command not found
wolfy@Stardust:~$ sudo del-apt-repository ppa:gdm2setup/gdm2setup
sudo: del-apt-repository: command not found
wolfy@Stardust:~$ sudo ppa-purge -repository ppa:gdm2setup/gdm2setup
sudo: ppa-purge: command not found
wolfy@Stardust:~$ sudo purge-apt-repository ppa:gdm2setup/gdm2setup
sudo: purge-apt-repository: command not found
wolfy@Stardust:~$ sudo ppa-purge
sudo: ppa-purge: command not found
wolfy@Stardust:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ppa-purge
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 5,218B of archives.
After this operation, 57.3kB of additional disk space will be used.
Get:1 http://ro.archive.ubuntu.com/ubuntu/ maverick/universe ppa-purge all 0.2.7.1+bzr53 [5,218B]
Fetched 5,218B in 0s (28.9kB/s)    
Selecting previously deselected package ppa-purge.
(Reading database ... 209956 files and directories currently installed.)
Unpacking ppa-purge (from .../ppa-purge_0.2.7.1+bzr53_all.deb) ...
Processing triggers for man-db ...
Setting up ppa-purge (0.2.7.1+bzr53) ...
wolfy@Stardust:~$ sudo ppa-purge -repository ppa:gdm2setup/gdm2setup
/usr/sbin/ppa-purge: illegal option -- r
Usage: sudo ppa-purge [options] <ppa:ppaowner>[/ppaname]

ppa-purge will reset all packages from a PPA to the standard
versions released for your distribution.

Options:
	-p [ppaname]		PPA name to be disabled (default: ppa)
	-s [host]		Repository server (default: ppa.launchpad.net)
	-d [distribution]	Override the default distribution choice.
	-h			Display this help text

Example usage commands:
	sudo ppa-purge xorg-edgers
	will remove https://launchpad.net/~xorg-edgers/+archive/ppa

	sudo ppa-purge -p xorg-testing sarvatt
	will remove https://launchpad.net/~sarvatt/+archive/xorg-testing

	sudo ppa-purge ppa:ubuntu-x-swat/x-updates
	will remove https://launchpad.net/~ubuntu-x-swat/+archive/x-updates

Notice: If ppa-purge fails for some reason and you wish to try again,
(For example: you left synaptic open while attempting to run it) simply
uncomment the PPA from your sources, run apt-get update and try again.

wolfy@Stardust:~$ sudo ppa-purge ppa:gdm2setup/gdm2setup
PPA to be removed: gdm2setup gdm2setup
Warning:  Could not find package list for PPA: gdm2setup gdm2setup
wolfy@Stardust:~$ sudo apt-get update
Hit http://ro.archive.ubuntu.com maverick Release.gpg
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/ maverick/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://ro.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ro.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://ro.archive.ubuntu.com maverick Release                    
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ro.archive.ubuntu.com maverick-updates Release                      
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://ro.archive.ubuntu.com maverick/main Sources                         
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ro.archive.ubuntu.com maverick/restricted Sources         
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ro.archive.ubuntu.com maverick/universe Sources           
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources  
Hit http://security.ubuntu.com maverick-security/main i386 Packages  
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Err http://ppa.launchpad.net maverick/main Sources                   
  404  Not Found
Hit http://ro.archive.ubuntu.com maverick/multiverse Sources         
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Hit http://ro.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://ro.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://ro.archive.ubuntu.com maverick/universe i386 Packages
Hit http://ro.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://ro.archive.ubuntu.com maverick-updates/main Sources
Hit http://ro.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://ro.archive.ubuntu.com maverick-updates/universe Sources
Hit http://ro.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://ro.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://ro.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://ro.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://ro.archive.ubuntu.com maverick-updates/multiverse i386 Packages
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
wolfy@Stardust:~$ sudo ppa-purge ppa:gdm2setup/gdm2setup

```

---

### Post by doctortonic on 2011-04-15
How can I remove that ppa? It;s usless, I could not install gdm setup 2 from there

---

### Post by hsoulen on 2011-04-15
> **doctortonic said:**
> How can I remove that ppa? It;s usless, I could not install gdm setup 2 from there

Administration-> Synaptic Package Manager
Settings->Repositories

Other Software tab

Find the PPA, highlight it and click "Remove"

Hank

---

### Post by doctortonic on 2011-04-15
Solved from synaptic / add/remove repro Thank You ! :)

---

### Post by johndoe32102002 on 2012-05-03
Since Synaptic is no longer updated, this method to remove PPAs no longer works.

If you try to use apt 0.9.2 and synaptic 0.75.10, you get this error in terminal:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named gtk.SoftwarePropertiesGtk

Any other solutions to remove PPAs (especially if you want to purge all and you don't know which PPAs are installed)?

---


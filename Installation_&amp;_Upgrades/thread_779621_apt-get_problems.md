---
title: "apt-get problems"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Hardrive on 2008-05-02
I can't do anything with apt-get, remove, install, anything:
```
jacob@xubuntu:~/downloads/oslib$ sudo apt-get install unrar
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 97.6kB of archives.
After this operation, 246kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/multiverse unrar 1:3.7.8-1 [97.6kB]
Fetched 97.6kB in 1s (71.1kB/s)                        
Selecting previously deselected package unrar.
(Reading database ... 100568 files and directories currently installed.)
Unpacking unrar (from .../unrar_1%3a3.7.8-1_amd64.deb) ...
Setting up automake (1:1.10.1-2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing automake (--configure):
 subprocess post-installation script returned error exit status 1
Setting up unrar (1:3.7.8-1) ...

[B]Errors were encountered while processing:
 automake[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

First, I tried removing automake, no dice.

After a bit of google, I tried apt-get -f install && dpkg --configure -a

---

### Post by Pumalite on 2008-05-02
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by Hardrive on 2008-05-02
That's the thing, it doesn't work.

```
acob@xubuntu:~/downloads/oslib$ sudo dpkg --configure -a
[sudo] password for jacob: 
Setting up automake (1:1.10.1-2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing automake (--configure):
 subprocess post-installation script returned error exit status 1
[B]Errors were encountered while processing:
 automake[/B]
jacob@xubuntu:~/downloads/oslib$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up automake (1:1.10.1-2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing automake (--configure):
 subprocess post-installation script returned error exit status 1
[B]Errors were encountered while processing:
 automake[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
jacob@xubuntu:~/downloads/oslib$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg          
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg   
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages   
Hit http://us.archive.ubuntu.com hardy/main Sources          
Hit http://us.archive.ubuntu.com hardy/restricted Sources    
Hit http://us.archive.ubuntu.com hardy/universe Packages     
Hit http://us.archive.ubuntu.com hardy/universe Sources      
Hit http://us.archive.ubuntu.com hardy/multiverse Packages   
Hit http://us.archive.ubuntu.com hardy/multiverse Sources    
Hit http://us.archive.ubuntu.com hardy-updates/main Packages 
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources  
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://security.ubuntu.com hardy-security Release.gpg    
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done
jacob@xubuntu:~/downloads/oslib$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libldap-2.4-2 lshw
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 498kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy-updates/main libldap-2.4-2 2.4.7-6ubuntu4.1 [197kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main lshw 02.12.01-2ubuntu1.1 [301kB]
Fetched 498kB in 2s (223kB/s)
(Reading database ... 100444 files and directories currently installed.)
Preparing to replace libldap-2.4-2 2.4.7-6ubuntu3 (using .../libldap-2.4-2_2.4.7-6ubuntu4.1_amd64.deb) ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace lshw 02.12.01-2ubuntu1 (using .../lshw_02.12.01-2ubuntu1.1_amd64.deb) ...
Unpacking replacement lshw ...
Setting up automake (1:1.10.1-2) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing automake (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libldap-2.4-2 (2.4.7-6ubuntu4.1) ...

Setting up lshw (02.12.01-2ubuntu1.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[B]Errors were encountered while processing:
 automake[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
jacob@xubuntu:~/downloads/oslib$ 
```

---

### Post by Pumalite on 2008-05-02
Try:
sudo dpkg --remove --force-remove-reinstreq automake

---

### Post by Hardrive on 2008-05-02
```
jacob@xubuntu:~/downloads/oslib$ sudo dpkg --remove --force-remove-reinstreq automake
[sudo] password for jacob: 
(Reading database ... 100443 files and directories currently installed.)
Removing automake ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing automake (--remove):
 subprocess pre-removal script returned error exit status 1
[B]Errors were encountered while processing:
 automake[/B]

```

---

### Post by Pumalite on 2008-05-02
Try:
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install automake

---

### Post by Hardrive on 2008-05-02
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install automake

Thanks so much, for some reason, that did the trick.

---

### Post by Pumalite on 2008-05-03
You are welcome. Good luck.

---


---
title: "installation of updates fail"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by dd000d on 2008-11-21
every time i try to install the updates for ubuntu(hard heron) it comes up with an error:

E: sub process /usr/bin/dpkg returned an error code (2)
A package failed to install


it wont install any of my 30 some updates... 
???? any help tried doing the update through the terminal but no luck there either

---

### Post by taurus on 2008-11-21
Can you post the complete error message when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dd000d on 2008-11-21
this is for the update... error on bottom

```
dan@dan-desktop:~$ sudo apt-get update
[sudo] password for dan: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release [1015B]                    
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [14.8kB]          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]              
Get:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages [1082B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Fetched 31.5kB in 46s (677B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

```


and this is for upgrade
```

dan@dan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  alacarte base-files dbus dbus-x11 firefox firefox-3.0 firefox-3.0-gnome-support
  firefox-gnome-support foo2zjs hpijs hplip hplip-data libdbus-1-3 libmysqlclient15off
  libsmbclient libxml2 libxml2-utils login logrotate module-init-tools mysql-common passwd
  python-apt python-libxml2 samba-common smbclient update-notifier update-notifier-common winbind
  wine wine-dev xulrunner-1.9 xulrunner-1.9-gnome-support
33 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9236kB/43.3MB of archives.
After this operation, 520kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://wine.budgetdedicated.com hardy/main wine-dev 1.1.9~winehq0~ubuntu~8.04-0ubuntu1 [1334kB]
Get:2 http://wine.budgetdedicated.com hardy/main wine 1.1.9~winehq0~ubuntu~8.04-0ubuntu1 [7903kB]  
Fetched 9236kB in 1min21s (113kB/s)                                                                
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19077 package `thunderbird':
 `Recommends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)
dan@dan-desktop:~$ 

```

---

### Post by taurus on 2008-11-21
You need to either update the key for "http://download.tuxfamily.org feisty Release" or comment it out in /etc/apt/sources.list for now.

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by dd000d on 2008-11-22
```
dan@dan-desktop:~$ cat /etc/apt/sources.list

deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
dan@dan-desktop:~$ 

```

---

### Post by taurus on 2008-11-22
I would edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the last two lines to comment them out.

```

**[COLOR="Blue"]#[/COLOR]**deb http://download.tuxfamily.org/3v1deb feisty eyecandy
**[COLOR="Blue"]#[/COLOR]**deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```
Save it and close down the gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dd000d on 2008-11-22
alright i put the # in front of the last two here is what i get for the updates

ok here is code for the update:

```
dan@dan-desktop:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg         
Hit http://archive.ubuntu.com hardy/universe Packages                          
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US        
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://archive.ubuntu.com hardy/main Packages                              
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Sources                    
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US 
Hit http://security.ubuntu.com hardy-security/restricted Sources              
Hit http://us.archive.ubuntu.com hardy Release                                
Hit http://security.ubuntu.com hardy-security/universe Packages               
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release                     
Hit http://us.archive.ubuntu.com hardy/main Sources                          
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Sources 
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Reading package lists... Done

```

here is the upgrade
```

dan@dan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  alacarte base-files dbus dbus-x11 firefox firefox-3.0
  firefox-3.0-gnome-support firefox-gnome-support foo2zjs hpijs hplip
  hplip-data libdbus-1-3 libmysqlclient15off libsmbclient libxml2
  libxml2-utils login logrotate module-init-tools mysql-common passwd
  python-apt python-libxml2 samba-common smbclient update-notifier
  update-notifier-common winbind wine wine-dev xulrunner-1.9
  xulrunner-1.9-gnome-support
33 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/43.3MB of archives.
After this operation, 520kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19077 package `thunderbird':
 `Recommends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

thanks for the help

---

### Post by taurus on 2008-11-22
Try something like

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, see if you can remove thunderbird.

```
sudo apt-get remove mozilla-thunderbird
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dd000d on 2008-11-22
ok heres what i get when i try to uninstall thunderbird

dan@dan-desktop:~$ sudo apt-get remove mozilla-thunderbird
[sudo] password for dan: 
Reading package lists... Error!
E: Problem parsing dependency Recommends
E: Error occurred while processing thunderbird (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by dd000d on 2008-12-19
?? haven't been able to even install programs for a month now

---


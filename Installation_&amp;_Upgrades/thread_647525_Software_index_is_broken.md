---
title: "Software index is broken"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by P&amp;P on 2007-12-22
[I]"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." [/I]

This is the response I am getting from update manager. After following the above the Synaptic method just doesn't work at all.  The Terminal method I get this:

"russ@FishTank:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-btdownload
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
 cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
 gnome-btdownload
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Any advice will be most welcomed. Using "Gutsy"
Many thx in anticipation

---

### Post by Pumalite on 2007-12-22
You could try:
sudo dpkg --remove --force-remove-reinstreq gnome-btdownload

---

### Post by P&amp;P on 2007-12-23
Pumalite thxs for your much needed  help.
Below is the out come following: "sudo dpkg --remove --force-remove-reinstreq gnome-btdownload" advice.  Does this help you to help me?
many thx



russ@FishTank:~$ sudo dpkg --remove --force-remove-reinstreq gnome-btdownload
[sudo] password for russ:
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
 cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
 gnome-btdownload
russ@FishTank:~$

---

### Post by Pumalite on 2007-12-23
Let's start from scratch:
sudo dpkg --configure -a (Enter)
sudo apt-get update (Enter)
sudo apt-get upgrade(Enter)
Post back with results.

---

### Post by P&amp;P on 2007-12-23
Below is the outcome. Good luck. Hope it makes sense.

russ@FishTank:~$ sudo dpkg --configure -a
russ@FishTank:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release 
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB     
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB       
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_GB  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                         
Get: 7 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]         
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Fetched 7B in 1s (4B/s)
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
russ@FishTank:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-btdownload
The following packages will be upgraded:
  apt apt-utils cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet findutils gimp gimp-data gimp-python hpijs
  hplip hplip-data kdelibs-data kdelibs4c2a libcupsimage2 libcupsys2 libdb4.4 libgimp2.0 libsmbclient
  linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic
  linux-ubuntu-modules-2.6.22-14-generic samba-common smbclient tomboy update-manager update-manager-core
30 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/79.5MB of archives.
After unpacking 684kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
 cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
 gnome-btdownload
E: Sub-process /usr/bin/dpkg returned an error code (1)
russ@FishTank:~$

---

### Post by Pumalite on 2007-12-23
Try:
sudo apt-get remove --purge gnome-btdownload

---

### Post by P&amp;P on 2007-12-24
Pumalite.
Below is the result, to the untrained eye I am none the wiser.  Good luck Pumalite. And thx for the help.

russ@FishTank:~$ sudo apt-get remove --purge gnome-btdownload
[sudo] password for russ:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gnome-btdownload
0 upgraded, 0 newly installed, 1 to remove and 30 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 496kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
 cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
 gnome-btdownload
E: Sub-process /usr/bin/dpkg returned an error code (1)
russ@FishTank:~$

---

### Post by PmDematagoda on 2007-12-24
Not sure about this as it maybe risky or may not work at all, but if you want to, try:-

```
sudo dpkg -r --force-all gnome-btdownload
```

---

### Post by P&amp;P on 2007-12-24
PmDematagoda

Thx below is the result.  Is there a way of physically removing this offending file?

russ@FishTank:~$ sudo dpkg -r --force-all gnome-btdownload
[sudo] password for russ:
(Reading database ... 101476 files and directories currently installed.)
Removing gnome-btdownload ...
dpkg: error processing gnome-btdownload (--remove):
 cannot remove file `/usr/share/man/man1/gnome-btdownload.1.gz': Not a directory
Errors were encountered while processing:
 gnome-btdownload
russ@FishTank:~$

---

### Post by Pumalite on 2007-12-24
Navigate to the file with, at the Terminal:
gksudo nautilus
And erase it.

---

### Post by P&amp;P on 2007-12-24
Pumalite

I've navigated using terminal.  What comes up is: "root-file browser" with "Desktop"folder icon. I then select  "View > show hidden files.....and I get a " .nautilus" folder  with other folders.  Inside the .nautilus folder is a "metafiles" folder.  Inside the metafiles there is nothing.  Do I delete this .nautilus file ? In fact is this the folder gksudo .nautilus?

Many questions. I admire your tenacity.

---

### Post by Pumalite on 2007-12-24
What you get with my command is just a File Browser with root privileges.
This is the place you have to go to:
/usr/share/man/man1/gnome-btdownload.1.gz
Delete: gnome-btdownload.1.gz

---

### Post by P&amp;P on 2007-12-24
Pumalite 
I now get from "Add/Remove Applications" and "Update Manager" the following having tried to update "You have 1 broken package on your system! Use the "Broken" filter to locate it"
Pumalite   please advice where I find "Broken filter to locate it?

P.S. I will need to move on in a very short while so let me wish you Pumalite and anyone else following this link/advice page "a happy christmas"

UPDATE

E: /var/cache/apt/archives/findutils_4.2.31-1ubuntu2.1_i386.deb: trying to overwrite `/usr/share/man/man5', which is also in package avahi-daemon
This followed Update Manager (I have 30 updates available) the above appears

---

### Post by Pumalite on 2007-12-24
Happy Christmas to you!
But, what happened with my previous advise?

---

### Post by P&amp;P on 2007-12-24
gnome-btdownload.1.gz 
was not in the folder or file

---

### Post by Pumalite on 2007-12-24
Go to Synaptic>Edit>Fix Broken Packages

---

### Post by P&amp;P on 2008-01-11
I've been away so to bring you up to date. I re-installed from scratch gusty.  My only thought why it went pear-shaped in the first place was due to me trying to deactivate Bit torrent using  the add/remove applications. Some food for thought why this caused such a pain in the neck and screwed up updates etc. 
A special thanks to Pumalite for sticking to the grindstone with his help and tenacity.

---

### Post by OpenBoel on 2008-02-28
I don't see if P&P has solved the problem...
I have been suffering with the same problem, so let me try to draw a final cut.

Do overcome the problem you should:

1. Remove all files beginning with the broken packet name (manually!)
2. Run synaptic to remove a broken packet entry.

That's all!                                                                           :KS

---


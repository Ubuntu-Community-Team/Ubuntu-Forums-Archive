---
title: "Holy APT-GET DPKG problems Batman"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by sosaudio1 on 2008-11-28
OK so the new kernel updates happened on my comp....went all the way thru and stopped at the checking step that it does at the end when you are updating...stopped as in hardlock no recovery. Pwr off then pwr on. Booted ok. Got some crazy..you have new hardware drivers message in the top bar..click it...get the drivers list??? Nothing to show how to update the drivers....Shut down and reboot normally. Go to Synaptic to check and get this:

E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: _cache->open() failed, please report.

So then go to terminal and sudo dpkg --configure -a

and get

dpkg: unable to open/create status database lockfile: No such file or directory

What gives? How do I fix?

Trust me, I have tried a number of commands....starting with

Now mind you these are the commands tried not necessarily all at once..

sudo cp /var/lib/dpkg/status.old /var/lib/dpkg/status

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old

sudo aptitude update

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

dpkg --clear-avail

sudo touch /var/lib/dpkg/lock

sudo apt-get update

sudo aptitude upgrade

pgrep dpkg

sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove


then it was  


rm /var/cache/apt/*.bin

sudo rm /var/cache/apt/*.bin

sudo rm /var/cache/apt/pkgcache.bin | sudo rm /var/cache/apt/srcpkgcache.bin

followed again by

sudo dpkg --configure -a

and still no joy...is there a way to rebuild???


What can I do to fix this????


It ***seems[I][B]***[/B][/I] as though it is in limbo. There seems to be no performance issues....yet....but, of course synaptic is out to lunch and I cannot get past the error. Cancel closes it....


Any help would be awesome
Thanks
Rich

---

### Post by sosaudio1 on 2008-11-29
Isn't there a way to force dpkg to flush and then update???

---

### Post by cdtech on 2008-11-29
Try this command:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
The **dpkg --configure** will reconfigure an unpacked package and the **apt-get -f** flag will fix broken packages.

---

### Post by sosaudio1 on 2008-11-29
> **cdtech said:**
> Try this command:
```
sudo dpkg --configure -a && sudo apt-get -f install
```


Thanks for responding
dpkg: unable to open/create status database lockfile: No such file or directory

---

### Post by cariboo on 2008-11-29
If you haven't got synaptic or Add/Remove Programs open, you shouldn't have any lock files in any of the /var/lib/dpkg. Instead of touching it you should have deleted it, because that is what is causing the error message

Jim

---

### Post by sosaudio1 on 2008-11-29
> **cariboo907 said:**
> If you haven't got synaptic or Add/Remove Programs open, you shouldn't have any lock files in any of the /var/lib/dpkg. Instead of touching it you should have deleted it, because that is what is causing the error message

Jim

got that....tried that earlier....how do i proceed?

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> got that....tried that earlier....how do i proceed?

should I

sudo rm /var/lib/dpkg/lock?

---

### Post by cdtech on 2008-11-29
> **sosaudio1 said:**
> Thanks for responding
dpkg: unable to open/create status database lockfile: No such file or directory

Have you tried:
```
sudo apt-get --fix-missing install
```

The old lock file....

---

### Post by sosaudio1 on 2008-11-29
> **cdtech said:**
> Have you tried:
```
sudo apt-get --fix-missing install
```

sudo apt-get --fix-missing install
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by cdtech on 2008-11-29
The only thing I can think of is:
```
sudo apt-get clean && sudo apt-get autoremove
```
If that doesn't do it, maybe a reboot and try to clean after the reboot.

---

### Post by sosaudio1 on 2008-11-29
> **cdtech said:**
> The only thing I can think of is:
```
sudo apt-get clean && sudo apt-get autoremove
```
If that doesn't do it, maybe a reboot and try to clean after the reboot.

sudo apt-get clean && sudo apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Will try again after reboot....looking at /var/lib/dpkg I have available, available-old, diversions, diversions-old, status, status.old (i made this one) and status-old

Diversions and diversions-old are script files the others are not...does that have any bearing??

Going down for reboot back in less that 10min


-------

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> sudo apt-get clean && sudo apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Will try again after reboot....looking at /var/lib/dpkg I have available, available-old, diversions, diversions-old, status, status.old (i made this one) and status-old

Diversions and diversions-old are script files the others are not...does that have any bearing??

Going down for reboot back in less that 10min


-------

back...in sys monitor killed update mgr and did:

sudo apt-get clean && sudo apt-get autoremove
[sudo] password for rich-and-lori: 
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Rich

---

### Post by sosaudio1 on 2008-11-29
sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory

what if I make /var/lib/dpkg change to dpkg.old and then create a empty dpkg directory?

Would it rebuild itself?

---

### Post by sosaudio1 on 2008-11-29
UGH!!!!!

sudo dpkg --configure -a
dpkg: unable to open/create status database lockfile: No such file or directory

---

### Post by cdtech on 2008-11-29
are you sure you have no lock?
```
-rw-r----- 1 root root        0 2008-11-05 18:55 lock
```
If not then do:
```
cd /var/lib/apt/lists
```
then:
```

sudo touch lock
sudo apt-get update

```

---

### Post by sosaudio1 on 2008-11-29
> **cdtech said:**
> are you sure you have no lock?
```
-rw-r----- 1 root root        0 2008-11-05 18:55 lock
```
If not then do:
```
cd /var/lib/apt/lists
```
then:
```

sudo touch lock
sudo apt-get update

```

Don't understand the first code...so I didn't do that one...more info...

Went into /var/lib/apt/lists via cd

Here is what the dir found.....look in particular to the locks...there are also partials....is this my problem



Many many thanks for getting this to work if we can...cuz...I cannot get anything to install....ok now for the pasting....


:/var/lib/apt/lists$ dir
apt.boxee.tv_dists_hardy_main_binary-i386_Packages
archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages
archive.canonical.com_ubuntu_dists_hardy_Release
archive.canonical.com_ubuntu_dists_hardy_Release.gpg
deb.mulx.net_dists_hardy_main_binary-i386_Packages
deb.mulx.net_dists_hardy_Release
deb.mulx.net_dists_hardy_Release.gpg
ftp.osuosl.org_pub_pculture.org_miro_linux_repositories_ubuntu_hardy_Packages
lock
packages.medibuntu.org_dists_hardy_free_binary-i386_Packages
packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages
packages.medibuntu.org_dists_hardy_Release
packages.medibuntu.org_dists_hardy_Release.gpg
partial
ppa.launchpad.net_exaile-devel_ubuntu_dists_hardy_main_binary-i386_Packages
ppa.launchpad.net_tualatrix_ubuntu_dists_hardy_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hardy-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_hardy-security_Release
security.ubuntu.com_ubuntu_dists_hardy-security_Release.gpg
security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hardy-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_hardy-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_Release
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy_Release
us.archive.ubuntu.com_ubuntu_dists_hardy_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_source_Sources


What do I need to do next????

---

### Post by sosaudio1 on 2008-11-29
if I did have a lock file beyond here in lists...cuz it looks like there is one, where would I find it...orrrrrr is this the problem and if it is, will the codes given fix it?

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> if I did have a lock file beyond here in lists...cuz it looks like there is one, where would I find it...orrrrrr is this the problem and if it is, will the codes given fix it?

there is a lock file in /var/lib/apt/lists

What is partial?

There is a directory folder there for partial...

---

### Post by sosaudio1 on 2008-11-29
anyone???

---

### Post by sosaudio1 on 2008-11-30
cd /var/lib/apt/lists
/var/lib/apt/lists$ sudo touch lock
[sudo] password 
/var/lib/apt/lists$ sudo apt-get update
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release.gpg
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Translation-en_US                           
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy Release                                          
Ign [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                    
Hit [http://apt.boxee.tv](http://apt.boxee.tv) hardy/main Packages                                    
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release.gpg                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Translation-en_US                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US        
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:1 [http://deb.mulx.net](http://deb.mulx.net) hardy Release.gpg [481B]                             
Ign [http://deb.mulx.net](http://deb.mulx.net) hardy/main Translation-en_US                           
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US  
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Get:3 [http://deb.mulx.net](http://deb.mulx.net) hardy Release [1133B]                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://deb.mulx.net](http://deb.mulx.net) hardy/main Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Get:5 [http://deb.mulx.net](http://deb.mulx.net) hardy/main Packages [354B]                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 1970B in 2s (910B/s)
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Freaking uncool.....how do I proceed?????

---

### Post by unutbu on 2008-11-30
Quit synaptic, or any other package manager app you may have open.
Then type the following commands in the terminal:
```
ls -l /var/lib/dpkg
sudo rm /var/lib/dpkg/lock
cd /var/lib/dpkg
sudo touch lock
sudo chmod 640 lock
ls -l /var/lib/dpkg
```

Then try using apt-get again.
If it doesn't work, please post the output of the above commands.

---

### Post by sosaudio1 on 2008-11-30
> **unutbu said:**
> Quit synaptic, or any other package manager app you may have open.
Then type the following commands in the terminal:
```
ls -l /var/lib/dpkg
sudo rm /var/lib/dpkg/lock
cd /var/lib/dpkg
sudo touch lock
sudo chmod 640 lock
ls -l /var/lib/dpkg
```

Then try using apt-get again.
If it doesn't work, please post the output of the above commands.


Not sure I have any synaptic or manager running. I have closed update manager which got rid of an apport issue I was having too...I think apport is showing that dpkg is unhappy and when I went back into system monitor just now apt-cache pops up then goes away...

Here is a copy of top:


                                                                                       
 5142 root      20   0  234m  25m 8100 S  1.7  2.6   3:01.44 Xorg                                                                                            
 7593 rich-and  20   0 73240  19m  10m R  0.6  1.9   0:00.60 gnome-terminal                                                                                  
 5689 rich-and  20   0  178m  60m  21m S  0.5  6.0   2:12.97 firefox                                                                                         
 7615 rich-and  20   0  2308 1116  852 R  0.3  0.1   0:00.06 top                                                                                             
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.54 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0                                                                                       
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  107 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
  141 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  142 root      20   0     0    0    0 S  0.0  0.0   0:00.06 pdflush                                                                                         
  143 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                         
  184 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1409 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1413 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1463 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 ata/0                                                                                           
 1465 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 1696 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 1698 root      15  -5     0    0    0 S  0.0  0.0   0:00.58 scsi_eh_1                                                                                       
 2455 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kjournald                                                                                       
 2658 root      16  -4  2528 1052  380 S  0.0  0.1   0:00.36 udevd                                                                                           
 2940 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 4065 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kjournald                                                                                       
 4066 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                                                       
 4336 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4337 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4341 root      20   0  1716  512  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4342 root      20   0  1716  508  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4344 root      20   0  1716  504  440 S  0.0  0.0   0:00.00 getty                                                                                           
 4512 root      20   0  2456 1356  692 S  0.0  0.1   0:00.00 acpid                                                                                           
 4557 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                     
 4625 syslog    20   0  1936  688  532 S  0.0  0.1   0:00.02 syslogd                                                                                         
 4678 root      20   0  1872  536  444 S  0.0  0.1   0:00.04 dd                                                                                              
 4680 klog      20   0  3256 2052  424 S  0.0  0.2   0:00.14 klogd                                                                                           
 4702 messageb  20   0  2892 1360  796 S  0.0  0.1   0:00.18 dbus-daemon                                                                                     
 4718 root      20   0 12776 2084 1820 S  0.0  0.2   0:00.02 NetworkManager                                                                                  
 4732 root      20   0  3416 1288 1124 S  0.0  0.1   0:00.00 NetworkManagerD                                                                                 
 4745 root      20   0  4112 1104  904 S  0.0  0.1   0:00.00 system-tools-ba                                                                                 
 4765 avahi     20   0  2760 1416 1204 S  0.0  0.1   0:00.02 avahi-daemon                                                                                    
 4766 avahi     20   0  2760  464  288 S  0.0  0.0   0:00.00 avahi-daemon                                                                                    
 4805 root      20   0  6032 2516 1900 S  0.0  0.2   0:00.02 cupsd  

Does it appear that I am running anything in the background that I am not aware of or is there a script or command list that I can run to make sure everything is down?

THANKS thanks thanks if you can help me get this running again

Rich

---

### Post by unutbu on 2008-11-30
You output from top looks fine.
Perhaps try those commands I posted previously, post the output from the terminal, and we'll go from there.

PS. top does not always show all the processes running on your machine. To get a complete list, type
```
ps axuww
```
However, I don't think that is really necessary in this case. If you've quit update-manager and synaptic, that is probably enough. If you want to be extra-sure, you could reboot, but again, I don't think that is really necessary.

---

### Post by sosaudio1 on 2008-11-30
$ ls -l /var/lib/dpkg
ls: cannot access /var/lib/dpkg/parts: No such file or directory
ls: cannot access /var/lib/dpkg/cmethopt: No such file or directory
ls: cannot access /var/lib/dpkg/lock: No such file or directory
ls: cannot access /var/lib/dpkg/statoverride-old: No such file or directory
ls: cannot access /var/lib/dpkg/triggers: No such file or directory
ls: cannot access /var/lib/dpkg/alternatives: No such file or directory
ls: cannot access /var/lib/dpkg/updates: No such file or directory
ls: cannot access /var/lib/dpkg/info: No such file or directory
ls: cannot access /var/lib/dpkg/statoverride: No such file or directory
total 6296
d????????? ? ?    ?          ?                ? alternatives
-rw-r--r-- 1 root root 1569255 2008-11-28 14:05 available
-rw-r--r-- 1 root root 1569255 2008-11-28 14:04 available-old
-????????? ? ?    ?          ?                ? cmethopt
-rw-r--r-- 1 root root      98 2008-10-10 12:56 diversions
-rw-r--r-- 1 root root     169 2008-10-10 12:56 diversions-old
d????????? ? ?    ?          ?                ? info
-????????? ? ?    ?          ?                ? lock
d????????? ? ?    ?          ?                ? parts
-????????? ? ?    ?          ?                ? statoverride
-????????? ? ?    ?          ?                ? statoverride-old
-rw-r--r-- 1 root root 1636543 2008-11-28 17:59 status
-rw-r--r-- 1 root root 1636543 2008-11-28 14:04 status-old
d????????? ? ?    ?          ?                ? triggers
d????????? ? ?    ?          ?                ? updates


This is just the first command obviously...do I proceed with remove lock?

---

### Post by unutbu on 2008-11-30
The output of the ls command should have looked more like this:
```
% ls -l /var/lib/dpkg
total 6724
drwxr-xr-x 2 root root    4096 2008-09-15 17:40 alternatives
-rw-r--r-- 1 root root 1660245 2008-11-30 06:29 available
-rw-r--r-- 1 root root 1660245 2008-11-30 06:29 available-old
-rw-r--r-- 1 root root       8 2007-10-15 19:17 cmethopt
-rw-r--r-- 1 root root    2915 2008-10-06 21:13 diversions
-rw-r--r-- 1 root root    2988 2008-06-11 16:34 diversions-old
drwxr-xr-x 2 root root  266240 2008-11-30 06:29 info
-rw-r----- 1 root root       0 2008-11-30 06:29 lock
drwxr-xr-x 2 root root    4096 2007-09-21 16:21 parts
-rw-r--r-- 1 root root      30 2008-07-14 16:03 statoverride
-rw-r--r-- 1 root root      58 2008-07-14 16:03 statoverride-old
-rw-r--r-- 1 root root 1614314 2008-11-30 06:29 status
-rw-r--r-- 1 root root 1614313 2008-11-30 06:29 status-old
drwxr-xr-x 2 root root    4096 2008-11-04 16:58 triggers
drwxr-xr-x 2 root root    4096 2008-11-30 06:29 updates

```

When you see a lot of question marks it is usually (always?) a sign that the filesystem is corrupt. 

Can you access your data on this machine? Can you back it up? There is a command that we could use to try to fix the filesystem (fsck) but I think it would be wise to back up your personal data first if possible.

---

### Post by sosaudio1 on 2008-11-30
> **unutbu said:**
> You output from top looks fine.
Perhaps try those commands I posted previously, post the output from the terminal, and we'll go from there.

PS. top does not always show all the processes running on your machine. To get a complete list, type
```
ps axuww
```
However, I don't think that is really necessary in this case. If you've quit update-manager and synaptic, that is probably enough. If you want to be extra-sure, you could reboot, but again, I don't think that is really necessary.

Thanks for that..do you want the output of ps axuww?

---

### Post by sosaudio1 on 2008-11-30
> **unutbu said:**
> The output of the ls command should have looked more like this:
```
% ls -l /var/lib/dpkg
total 6724
drwxr-xr-x 2 root root    4096 2008-09-15 17:40 alternatives
-rw-r--r-- 1 root root 1660245 2008-11-30 06:29 available
-rw-r--r-- 1 root root 1660245 2008-11-30 06:29 available-old
-rw-r--r-- 1 root root       8 2007-10-15 19:17 cmethopt
-rw-r--r-- 1 root root    2915 2008-10-06 21:13 diversions
-rw-r--r-- 1 root root    2988 2008-06-11 16:34 diversions-old
drwxr-xr-x 2 root root  266240 2008-11-30 06:29 info
-rw-r----- 1 root root       0 2008-11-30 06:29 lock
drwxr-xr-x 2 root root    4096 2007-09-21 16:21 parts
-rw-r--r-- 1 root root      30 2008-07-14 16:03 statoverride
-rw-r--r-- 1 root root      58 2008-07-14 16:03 statoverride-old
-rw-r--r-- 1 root root 1614314 2008-11-30 06:29 status
-rw-r--r-- 1 root root 1614313 2008-11-30 06:29 status-old
drwxr-xr-x 2 root root    4096 2008-11-04 16:58 triggers
drwxr-xr-x 2 root root    4096 2008-11-30 06:29 updates

```

When you see a lot of question marks it is usually (always?) a sign that the filesystem is corrupt. 

Can you access your data on this machine? Can you back it up? There is a command that we could use to try to fix the filesystem (fsck) but I think it would be wise to back up your personal data first if possible.

Haven't gone real deep but looks like I can...let me copy some things to sdb1

---

### Post by drs305 on 2008-11-30
You might try doing a search on your system for all locks to see if you missed one somewhere:
```

sudo find / -type f -iname lock

```

---

### Post by sosaudio1 on 2008-11-30
> **drs305 said:**
> You might try doing a search on your system for all locks to see if you missed one somewhere:
```

sudo find / -type f -iname lock

```

just a heads-up....system borked on copy of /home to sdb1 hardlock no joy pwr off to come up to auto ckfs fails to manual fs failing on not connecting to lost and found to should be 1 is 2 fix(y)? to several files fix seemed like no end....booted live CD made copies of important folders and files to sdb1 and reinstalled

System up to update synaptic running found 195 updates....start update...walk away...back..system dl'd all updates hardlocked on some installs....reboot using pwr...synaptic calls for right click start or terminal apt-get....right click failed to start...err...dpkg --configure -a

sudo dpkg --configure -a works, apt-get clean works, apt-get upgrade...works, apt-get update works....reboot due to killing update manager reason - may need reboot for updated files....reboot works, update manager shows 16 needed files bind in list as well as kernel updates...using caution on reinstalls of updates, selected only kernel install updates...works...reboot called for and updates noted....rebooted...works, updated bind and related called for...works...


system up


did last command asked for in thread here


results

sudo find / -type f -iname lock

find: /home/rich-and-lori/.gvfs: Permission denied
/proc/sys/dev/cdrom/lock
/var/lib/dpkg/triggers/Lock
/var/lib/dpkg/lock
/var/lib/apt/lists/lock
/var/cache/apt/archives/lock
/root/.synaptic/lock


look good or bad result?

---

### Post by unutbu on 2008-11-30
I get the same result from the "sudo find" command.
If everything seems to be working, I'd say you are good to go.

---

### Post by sosaudio1 on 2008-11-30
> **unutbu said:**
> I get the same result from the "sudo find" command.
If everything seems to be working, I'd say you are good to go.

think everything is working where is the fingers crossed smilie?

I'm not gonna close this one yet...tho

---


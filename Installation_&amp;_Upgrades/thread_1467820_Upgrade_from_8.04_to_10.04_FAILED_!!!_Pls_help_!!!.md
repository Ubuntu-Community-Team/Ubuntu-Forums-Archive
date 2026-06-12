---
title: "Upgrade from 8.04 to 10.04 FAILED !!! Pls help !!!"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by kkfok1 on 2010-05-01
I have problem to upgrade from 8.04 to 10.04 (using the CD burned with downloaded 386-iso, have check md5sum which is correct) 

The error that I had found in the var/log/dist-upgrade/main.log are as following :

Any advise to solve this is very much appreciated.

Thanks

2010-05-01 13:47:16,297 INFO Using config files '['./DistUpgrade.cfg.hardy']'
2010-05-01 13:47:16,297 INFO uname information: 'Linux blissful 2.6.24-27-generic #1 SMP Wed Mar 24 10:04:52 UTC 2010 i686'
2010-05-01 13:47:16,297 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-05-01 13:47:16,474 INFO release-upgrader version '0.134.7' started
2010-05-01 13:47:16,729 DEBUG svg pixbuf loader failed (Error displaying image)
2010-05-01 13:47:16,729 [COLOR="Blue"]ERROR html widget
Traceback (most recent call last):
File "/tmp/tmp.blmGi13183/DistUpgradeViewGtk.py", line 404, in __init__
import webkit
ImportError: No module named webkit[/COLOR]
2010-05-01 13:47:16,743 DEBUG Using 'DistUpgradeViewGtk' view



(some logs in between)



2010-05-01 13:47:42,392 DEBUG doUpdate() will not use the network because self.useNetwork==false
2010-05-01 13:47:42,393 DEBUG openCache()
2010-05-01 13:47:42,771 DEBUG /openCache(), new cache size 2289
2010-05-01 13:47:42,771 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-05-01 13:48:24,805 [COLOR="Blue"]ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'[/COLOR]
2010-05-01 13:48:24,805 DEBUG abort called
2010-05-01 13:48:24,807 DEBUG openCache()
2010-05-01 13:48:27,829 DEBUG /openCache(), new cache size 25405
2010-05-01 13:48:27,830 DEBUG enabling apt cron job

---

### Post by kkfok1 on 2010-05-01
BTW, I have already used update manager to have the 8.04 system up todate.

---

### Post by kkfok1 on 2010-05-01
I checked the alternate iso file was dated 27th April, was this the problem ?

---

### Post by kkfok1 on 2010-05-04
Hello, can someone please help !

Thanks

---

### Post by kkfok1 on 2010-05-04
What is happening ? Seems there is no one care about this ?

---

### Post by pgmer6809 on 2010-05-07
I was about to do the same thing. Now I won't. My problem is that I am not sure how to do the alternative of a fresh install without losing too much of what I have now. 

I dont have an answer for your problem other than to say that:
In the past I have been advised against skipping generations.
This should have been fixed. Obviously an LTS user is not going to want to have to install the intermediate distros to get from one LTS distro to the next.
Maybe you can contact the Ubuntu support page (Canonical not just the forums) on this.

1) Advice elsewhere is to steer clear of dist-upgrade. There seem to be lots of problems with it.
2) Same advice says to:
a) back everything up. I am guessing this means /home, If you backup and restore /etc and so on, how will you restore them without overwriting the new stuff?
That being the case you probably do want to make a record of the packages you have on your current system so that you can automatically  re-install them after the fresh Lynx install.

b) install new system from scratch.

c) Restore from backup

d) restore packages.

3) To save the list of packages you now have, do this:

```
dpkg --get-selections > installed-software
```

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,


```
dpkg --set-selections < installed-software
```

followed by


```
dselect
```

4. If you want to try one more time with the dist-upgrade feature, you can try this from the cmd line (again based on another thread. I have not tried this myself.):
(Best to do backups first though. /home, the package list etc. as above.)

switch into super user.
```
sudo su    
cd /etc/apt/
cp sources.list sources.list.hardy.backup
sed -e 's/hardy/lucid/' sources.list >>sources.list.lucid
cp sources.list.lucid sources.list
apt-get clean
apt-get update
apt-get dist-upgrade
exit
```

good luck.

---

### Post by kkfok1 on 2010-05-11
Hi pgmer6809,

Thank you for taking time reponse to my problem and I'll consider your suggestion carefully -- fresh installation.

I have posted this to launchpad but did not receive any replies. Seems that Ubuntu team are so busy to solve the 10.04 problems. :(

---

### Post by gannite6364 on 2010-05-11
Sorry i have not replyed to your post before only just seen it. Your problem is that you can not upgrade from 8.04 to 10.04. You can only do it one step at a time ie from 8.04 to 9.04 and so on.

---

### Post by jmaryinchina on 2010-05-11
It looks like you have some packages you have installed manually which are making problems.

I suggest that you fix everything from the terminal from now and forget about the update manager.

[LIST=1]
[*]First of all, provide the file /etc/apt/sources.list here to check if the sources.list refers now to lucid  or if it is still referring to 8.04.
[*]If you are sure about the above, no need to transmit here the sources.list. Proceed the following command : ```
sudo apt-get update && sudo apt-get dist-upgrade
```
[*] copy paste the result here, thus we can see in detail what is going on.
[/LIST]

---

### Post by jmaryinchina on 2010-05-11
> **gannite6364 said:**
> Sorry i have not replyed to your post before only just seen it. Your problem is that you can not upgrade from 8.04 to 10.04. You can only do it one step at a time ie from 8.04 to 9.04 and so on.
gannite6364 : you said something wrong. Upgrades are possible from an LTS version to another LTS version.

---

### Post by gannite6364 on 2010-05-11
Yes sorry about that was not thinking straight.

---

### Post by kkfok1 on 2010-05-12
> **jmaryinchina said:**
> It looks like you have some packages you have installed manually which are making problems.

I suggest that you fix everything from the terminal from now and forget about the update manager.

[LIST=1]
[*]First of all, provide the file /etc/apt/sources.list here to check if the sources.list refers now to lucid  or if it is still referring to 8.04.
[*]If you are sure about the above, no need to transmit here the sources.list. Proceed the following command : ```
sudo apt-get update && sudo apt-get dist-upgrade
```
[*] copy paste the result here, thus we can see in detail what is going on.
[/LIST]
Output of  sudo apt-get update && sudo apt-get dist-upgrade


Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100318) lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100318) lucid/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg                                      
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://winff.org](http://winff.org) hardy Release.gpg                                         
Ign [http://winff.org](http://winff.org) hardy/universe Translation-en_US                          
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release                                          
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US         
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release.gpg                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://winff.org](http://winff.org) hardy Release                                             
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Packages                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Translation-en_US            
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Packages                                  
Hit [http://winff.org](http://winff.org) hardy/universe Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Sources   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 11.9kB in 3s (3798B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  build-essential dpkg-dev g++
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by kkfok1 on 2010-06-09
Finally, I have to reinstall Lucid instead of using the Alternate CD to upgrade.

---

### Post by satish_j on 2010-08-16
Iam facing the same issue..And feeling very sad that No solution has been found for it so far:(:(

---


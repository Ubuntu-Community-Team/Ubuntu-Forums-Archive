---
title: "Update manager could not be updated. (Didn't Alanis Morrisette sing about this?)"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by MSdefecter on 2008-05-16
Hi,
I just re-installed Ubuntu 7.10 and saw that 8.04 was available for upgrade. I decided to upgrade but it has been a pain so far. While the upgrade was taking place a warning came up telling me that update manager was unable to be updated, ironically. Whenever I try to use update manager it shows no upgrades and the message "It is unknown when the packet information was updated last. Please try clicking on the 'check' button to update the information." When I do this it shows a progress bar and the message that is downloading 24 packages but it always freezes on 15. I now however am unable to download any programs using the install and remove applications utility. I have tried re-installing the update manager but to no avail and when using the apt get commands in the terminal I get the same lack of success. Does anyone have any ideas to help?

---

### Post by overdrank on 2008-05-16
> **MSdefecter said:**
> Hi,
I just re-installed Ubuntu 7.10 and saw that 8.04 was available for upgrade. I decided to upgrade but it has been a pain so far. While the upgrade was taking place a warning came up telling me that update manager was unable to be updated, ironically. Whenever I try to use update manager it shows no upgrades and the message "It is unknown when the packet information was updated last. Please try clicking on the 'check' button to update the information." When I do this it shows a progress bar and the message that is downloading 24 packages but it always freezes on 15. I now however am unable to download any programs using the install and remove applications utility. I have tried re-installing the update manager but to no avail and when using the apt get commands in the terminal I get the same lack of success. Does anyone have any ideas to help?

HI and was the 7.10 version updated before the upgrade to 8.04? Could you post the output of the commands in the terminal 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by MSdefecter on 2008-05-16
Hi,
7.10 was according to the update manager fully updated before I installed 8.04 like it instructs you to do. The only thing showing in the update manager was the option to upgrade to 8.04. Anyway here are the outputs for the above commands.

sudo apt-get update

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Reading package lists... Done                             
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by overdrank on 2008-05-16
Ok have you tried and change the location of the server in system, administration, software sources.

---


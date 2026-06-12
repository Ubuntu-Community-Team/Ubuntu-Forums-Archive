---
title: "Upgrading from 7.10 to 9.10 on Ubuntu Server"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by mickey78 on 2010-02-25
Hello everyone!

I have a server running Ubuntu 7.10 that I really want to upgrade to 9.10, unfortunately, I didn't follow the upgrade flow and now 7.10 is unsupported wich means I cannot contact the repository anymore. What would be the best way to upgrade this box? I tried the usual sudo do-release-upgrade but I get a bunch of error when the server tries to contact the gutsy repositories. I just want to make sure it is safe. Here is my output

lgarceau@cnqweb:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
lgarceau@cnqweb:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lgarceau@cnqweb:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmpP24Xvx/hardy.tar.gz'
authenticate '/tmp/tmpP24Xvx/hardy.tar.gz' against '/tmp/tmpP24Xvx/hardy.tar.gz.gpg' 

Reading cache

Checking package manager

Continue running under SSH? 

This session appears to be running under ssh. It is not recommended 
to perform a upgrade over ssh currently because in case of failure it 
is harder to recover. 

If you continue, a additional ssh daemon will be started at port 
'9004'. 
Do you want to continue? 

Continue [yN] y

Starting additional sshd 

To make recovery in case of failure easier a additional sshd will be 
started on port '9004'. If anything goes wrong with the running ssh 
you can still connect to the additional one. 


Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy Release.gpg
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy Release.gpg
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates Release.gpg
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy Release
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates Release
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Sources
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Packages
Ignored [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/main Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/restricted Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/universe Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy/multiverse Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/main Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/restricted Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/universe Sources
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Packages
Failed [http://mirror.anl.gov](http://mirror.anl.gov) gutsy-updates/multiverse Sources
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release.gpg
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Done [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy/multiverse Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/universe Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/multiverse Sources
Done downloading            

Checking package manager
Reading package lists: Donehardy-security/multiverse Packages: 98  
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Do you want to start the upgrade? 


1 package is going to be removed. 28 new packages are going to be 
installed. 298 packages are going to be upgraded. 

You have to download a total of 185M. This download will take about 2 
minutes with your connection. 

Fetching and installing the upgrade can take several hours. Once the 
download has finished, the process cannot be cancelled.

---

### Post by mörgæs on 2010-02-26
As far as I know there is no other option than doing a clean install - which I would recommend anyway! 

If the machine works you could wait a few months until 10.04 (long time support) is ready.

---

### Post by dvlchd3 on 2010-02-26
Actually, I believe you can upgrade to 8.04LTS, from 8.04, you can upgrade to 9.10. (Or any release after 8.04 for that matter).  However, I believe you may need to download the 8.04 CD and enable the CD repository to upgrade.  I have never upgraded an unsupported version of Ubuntu before, can someone else verify this?  Is it still possible to do a network upgrade from a version that is no longer supported?

---

### Post by mickey78 on 2010-02-26
For everyone's information I tried it in my VMWARE server and it worked. It gives some error at begining about the repos, but the upgrade works. Thanks.

---


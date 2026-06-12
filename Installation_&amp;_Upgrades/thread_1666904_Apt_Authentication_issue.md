---
title: "Apt Authentication issue"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by ranger_cole on 2011-01-14
I am using Ubuntu 8.04 and still getting some updates but I have been having Apt Authentication issues:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release](http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.

What does this mean and how do I fix it?  

I switched to the main server in (System>Admin>Software Sources but still no joy.
Thanks for helping in advance.

---

### Post by Rubi1200 on 2011-01-14
Hardy has already reached its end of life, meaning that official updates are no longer available.

You could try this though:
 you can try the old-releases repos: [http://soniahamilton.wordpress.com/2...ons-of-ubuntu/]("http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/")

---

### Post by ranger_cole on 2011-01-14
Do I add it to software sources( Not sure how to do this)? Or do you open the directories and manually download?  I looked and did not see a Hardy directory?????

---

### Post by Rubi1200 on 2011-01-14
This is odd to say the least!

I saw someone on the forum the other day link to the same thing I gave you and the thread starter posted back that they had manually added the repositories for **Hardy** and everything was working!?!

Give me some time please and I will get this figured out for you.

---

### Post by plucky on 2011-01-14
> **Rubi1200 said:**
> Hardy has already reached its end of life, meaning that official updates are no longer available.

You could try this though:
 you can try the old-releases repos: [http://soniahamilton.wordpress.com/2...ons-of-ubuntu/]("http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/")

Hardy doesn't reach END_OF _LIFE until April 2011 as it is a LTS Release.

See [Here](https://wiki.ubuntu.com/Releases)


Good Luck

---

### Post by Rubi1200 on 2011-01-14
My mistake :oops:, you are absolutely right plucky.

In hindsight, I think what I saw before was for Intrepid (which has reached EOL).

@ranger_cole:

if you are having problems updating try this:

```
sudo dpkg --configure -a

sudo apt-get update
```

Post back if there are errors.

---

### Post by oldos2er on 2011-01-14
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 54422A4B98AB5139 && sudo apt-key adv --keyserver keyserver.ubuntu.com 4874D3686E80C6B7
```

---

### Post by oldos2er on 2011-01-14
*sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID*

where *KEYID* is number shown in error msg

---

### Post by ranger_cole on 2011-01-14
I cannot try the fix until Monday.  I will post back after I give it a go.

---

### Post by ranger_cole on 2011-01-17
I tried both suggestions and still get the error messages.  I guess I will have to live with it or upgrade to 10.04 LTS.  Thanks for the suggestions and ideas.

---

### Post by plucky on 2011-01-17
> **ranger_cole said:**
> I tried both suggestions and still get the error messages.  I guess I will have to live with it or upgrade to 10.04 LTS.  Thanks for the suggestions and ideas.

Is the error the same or has it changed?
Post complete output of ```
sudo apt-get update
```

What happened when you used the commands suggested by oldos2r?

---

### Post by ranger_cole on 2011-01-17
Here is the code after running the two suggestions:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/hardy-backport/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/hardy-backport/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/hardy-backport/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/hardy-backport/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release](http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dino99 on 2011-01-17
why not using the main server and download virtualbox from Oracle ?

---

### Post by ranger_cole on 2011-01-17
I was on the main server and was getting the errors so it was suggested, in this thread, I switch to the server I am pointing to now.

---

### Post by plucky on 2011-01-17
> W: Failed to fetch [http://archive.ubuntu-rocks.org/ubun...tion-en_US.bz2](http://archive.ubuntu-rocks.org/ubun...tion-en_US.bz2) Could not resolve 'archive.ubuntu-rocks.org'

When I click on the links in your post I get **Server Not Found**.

Please post your sources.list ```
cat /etc/apt/sources.list
```

and your other sources ```
ls -l /etc/apt/sources.list.d
```

---

### Post by oldos2er on 2011-01-17
> **ranger_cole said:**
> I tried both suggestions and still get the error messages.  I guess I will have to live with it or upgrade to 10.04 LTS.  Thanks for the suggestions and ideas.

Can you run the command ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4874D3686E80C6B7
``` and post the output?

---

### Post by ranger_cole on 2011-01-17
here is the output for sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4874D3686E80C6B7:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: public key "Launchpad PPA for Banshee Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

---

### Post by ranger_cole on 2011-01-17
Here is the the other output:

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy main restricted hardy-backport

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-updates main restricted hardy-backport

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy universe
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy multiverse
deb [http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe hardy-backport
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Eternity Screensaver
deb [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main
deb-src [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
## Depôt MultiSystem
deb [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all main


 ls -l /etc/apt/sources.list.d
total 32
-rw-r--r-- 1 root root 176 2011-01-14 09:25 google-chrome.list
-rw-r--r-- 1 root root 176 2011-01-14 09:25 google-chrome.list.save
-rw-r--r-- 1 root root 225 2011-01-14 09:25 medibuntu.list
-rw-r--r-- 1 root root 225 2011-01-14 09:25 medibuntu.list.save
-rw-r--r-- 1 root root 353 2011-01-14 09:25 opera.list
-rw-r--r-- 1 root root 353 2011-01-14 09:25 opera.list.save
-rw-r--r-- 1 root root   1 2011-01-14 09:25 spideroak.com.sources.list
-rw-r--r-- 1 root root   1 2011-01-14 09:25 spideroak.com.sources.list.save
jaypugh@jaypugh-desktop:~$

---

### Post by plucky on 2011-01-17
[http://archive.ubuntu-rocks.org/ubuntu/](http://archive.ubuntu-rocks.org/ubuntu/)

Still cannot get to that server.

Switch back to the main server and see if that fixes the problem.

The GPG key for launchpad has been accepted.

After you have switched back to the Main Server,post the output of ```
sudo apt-get update
```

---

### Post by ranger_cole on 2011-01-18
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release.gpg [197B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Translation-en_US            
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Get:4 [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release [5447B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Err [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release                               
  
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1091B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://liveusb.info](http://liveusb.info) all Release.gpg                                        
Ign [http://liveusb.info](http://liveusb.info) all/main Translation-en_US                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/hardy-backport Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/hardy-backport Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/hardy-backport Translation-en_US 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy Release.gpg                                     
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Translation-en_US                          
Hit [http://liveusb.info](http://liveusb.info) all Release                                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy Release                                         
Ign [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages   
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Fetched 2833B in 2s (951B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release](http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by plucky on 2011-01-18
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

From a terminal ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 54422A4B98AB5139
``` should get rid of that warning.

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)


I would go into Software Sources and disable the Hardy Backports repository and see if that fixes the problem.

Good Luck

---

### Post by ranger_cole on 2011-01-18
I did not see a line, in Software sources, that lists:

I would go into Software Sources and disable the Hardy Backports repository and see if that fixes the problem.

Also here is the new output after trying your suggestion:  sudo apt-get update

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release](http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by dino99 on 2011-01-18
sudo rm /var/cache/apt/archives/*

open synaptic repo tab (third party)

change the virtualbox url to:
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib

then update upgrade

---

### Post by dino99 on 2011-01-18
sudo rm /var/cache/apt/archives/*

open synaptic repo tab (third party)

change the virtualbox url to:
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib

then update upgrade

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox)

---

### Post by ranger_cole on 2011-01-18
Here is what I get after:  sudo rm /var/cache/apt/archives/*

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

Also when I try to edit the virtualbox source the ok button become unclickable.  Cannot save changes.

---

### Post by ranger_cole on 2011-01-18
Here is what I get after:  sudo rm /var/cache/apt/archives/*

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

Also when I try to edit the virtualbox source the ok button become unclickable.  Cannot save changes.

---

### Post by ranger_cole on 2011-01-18
Here is what I get after:  sudo rm /var/cache/apt/archives/*

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

Also when I try to edit the virtualbox source the ok button become unclickable.  Cannot save changes.

---

### Post by MX5EdL on 2011-01-29
Were you able to fix this issue?

I am running the same version and receiving the same error messages.  I also tried the earlier recommendations without success.

---

### Post by ranger_cole on 2011-01-29
Not yet.  I am stumped.

---

### Post by oldos2er on 2011-01-29
> **ranger_cole said:**
> Here is what I get after:  sudo rm /var/cache/apt/archives/*

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

Run ```
gksu nautilus
``` Delete everything in /var/cache/apt/archives (except for the archives folder itself). 

> **ranger_cole said:**
> Also when I try to edit the virtualbox source the ok button become unclickable.  Cannot save changes.

While you're still in admin mode nautilus, open /etc/apt/sources.list in gedit. Change

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

to

[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy contrib

Save and exit the file, close nautilus, run ```
sudo apt-get update
``` If there are any further errors, please post them here in full.

---

### Post by ranger_cole on 2011-01-31
I followed your instructions and here is what i get now when i try to update:
E: Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by ranger_cole on 2011-01-31
I fixed the partial missing error and here is my output when I run update :

jaypugh@jaypugh-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jaypugh@jaypugh-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Get:3 [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release.gpg [197B]                  
Get:4 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [198B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [198B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://download.virtualbox.org](http://download.virtualbox.org) hardy/contrib Translation-en_US             
Get:8 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/hardy-backport Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [198B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/hardy-backport Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Get:10 [http://parker1.co.uk](http://parker1.co.uk) hardy Release.gpg [197B]                           
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Translation-en_US                          
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/hardy-backport Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:12 [http://liveusb.info](http://liveusb.info) all Release.gpg [490B]                              
Ign [http://liveusb.info](http://liveusb.info) all/main Translation-en_US                             
Get:13 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                             
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy Release                                         
Get:14 [http://deb.opera.com](http://deb.opera.com) stable Release [1063B]                             
Get:15 [http://download.virtualbox.org](http://download.virtualbox.org) hardy/contrib Packages [1009B]           
Err [http://deb.opera.com](http://deb.opera.com) stable Release                                        
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Get:17 [http://dl.google.com](http://dl.google.com) stable/main Packages [1110B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://liveusb.info](http://liveusb.info) all Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources                                    
Ign [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages                                   
Hit [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Fetched 6638B in 3s (2195B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
jaypugh@jaypugh-desktop:~$

---

### Post by oldos2er on 2011-01-31
For the NO_PUBKEY error, run the command shown in post #21, and replace the KEYID number at the end with the KEYID shown in the error message.

I don't have any problem loading the URLs given in the 'failed to fetch' warnings. Have you tried different servers?

---

### Post by ranger_cole on 2011-01-31
Where do I need to go edit the KEY ID?  I am not clear on how to do this.

---

### Post by oldos2er on 2011-01-31
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
``` is the command you need to run. 

The KeyID is the 16 character alphanumeric shown in the warning *W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8*

---

### Post by ranger_cole on 2011-02-01
Here is the output after following instructions:

jaypugh@jaypugh-desktop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys A2019EA84E7532C8
gpg: requesting key 4E7532C8 from hkp server keyserver.ubuntu.com
gpg: key 4E7532C8: "Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>" not changed
gpg: Total number processed: 1
gpg:              imported: 1

jaypugh@jaypugh-desktop:~$ sudo apt-get update
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release.gpg
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://download.virtualbox.org](http://download.virtualbox.org) hardy/contrib Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://liveusb.info](http://liveusb.info) all Release.gpg                                        
Ign [http://liveusb.info](http://liveusb.info) all/main Translation-en_US                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/hardy-backport Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/hardy-backport Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/hardy-backport Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy Release.gpg                                     
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Translation-en_US                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://liveusb.info](http://liveusb.info) all Release                                            
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy Release                                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1099B]                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy/contrib Packages                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources                                    
Hit [http://liveusb.info](http://liveusb.info) all/main Packages                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://parker1.co.uk](http://parker1.co.uk) hardy/main Sources                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources  
Fetched 2643B in 3s (720B/s)                              
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  hardy-backport/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

As you can see i ran update command and have included the output.

---

### Post by oldos2er on 2011-02-01
You could either disable backports, or try different servers.

---


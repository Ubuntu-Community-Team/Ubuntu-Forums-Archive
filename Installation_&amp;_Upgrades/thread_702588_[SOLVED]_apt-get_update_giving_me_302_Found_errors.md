---
title: "[SOLVED] apt-get update giving me 302 Found errors for ubuntu.com sites"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Levander on 2008-02-20
Whenever I do an 'apt-get update' command on my system, apt-get is giving me "302 Found" errors.  I have no idea how to get rid of them and update the deb indexes on my system.

I think this situation started when I installed Gutsy from the LiveCD.  I remember there was some error about "can't retrieve security updates".  I had just built the computer from various hardware pieces and found out I hadn't plugged in the network cable.  So, I plugged it in next time I wanted to use apt-get and successfully installed some new package.  I didn't try a 'apt-get update' at that time.

Here's the output of 'apt-get update', the errors are toward the end:

```

Get:1 http://packages.medibuntu.org gutsy Release.gpg [189B]                                                             
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                                                           
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US                                                       
Hit http://packages.medibuntu.org gutsy Release                                                                          
Ign http://packages.medibuntu.org gutsy/free Packages                                                                    
Ign http://packages.medibuntu.org gutsy/non-free Packages                                                       
Hit http://packages.medibuntu.org gutsy/free Packages                                                           
Hit http://packages.medibuntu.org gutsy/non-free Packages                                                       
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                                                        
Hit http://archive.ubuntu.com gutsy Release                                                        
Hit http://archive.ubuntu.com gutsy/main Sources                                                  
Hit http://archive.ubuntu.com gutsy/restricted Sources                       
Ign http://us.archive.ubuntu.com gutsy Release.gpg                                                                       
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                                                            
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US                                                      
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                                        
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US                                                      
Ign http://us.archive.ubuntu.com gutsy-updates Release.gpg                                                               
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US                                                    
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US                                              
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US                                                
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                                              
Ign http://us.archive.ubuntu.com gutsy Release                                                                           
Ign http://us.archive.ubuntu.com gutsy-updates Release                                                                   
Ign http://us.archive.ubuntu.com gutsy/main Packages                                                                     
Ign http://us.archive.ubuntu.com gutsy/restricted Packages                                                               
Ign http://us.archive.ubuntu.com gutsy/restricted Sources                                                                
Ign http://us.archive.ubuntu.com gutsy/main Sources                                                                      
Ign http://us.archive.ubuntu.com gutsy/multiverse Sources                                                                
Ign http://us.archive.ubuntu.com gutsy/universe Sources                                                                  
Ign http://us.archive.ubuntu.com gutsy/universe Packages                                                                 
Ign http://us.archive.ubuntu.com gutsy/multiverse Packages                                                               
Ign http://us.archive.ubuntu.com gutsy-updates/main Packages                                                             
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Packages                                                       
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Sources                                                        
Ign http://us.archive.ubuntu.com gutsy-updates/main Sources                                                              
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Sources                                                        
Ign http://us.archive.ubuntu.com gutsy-updates/universe Sources                                                          
Ign http://us.archive.ubuntu.com gutsy-updates/universe Packages                                                         
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Packages                                                       
Err http://us.archive.ubuntu.com gutsy/main Packages                                                                     
  302 Found
Err http://us.archive.ubuntu.com gutsy/restricted Packages                                                               
  302 Found
Err http://us.archive.ubuntu.com gutsy/restricted Sources                                                                
  302 Found
Err http://us.archive.ubuntu.com gutsy/main Sources                                                                      
  302 Found
Err http://us.archive.ubuntu.com gutsy/multiverse Sources                                                                
  302 Found
Err http://us.archive.ubuntu.com gutsy/universe Sources                                                                  
  302 Found
Err http://us.archive.ubuntu.com gutsy/universe Packages                                                                 
  302 Found
Err http://us.archive.ubuntu.com gutsy/multiverse Packages                                                               
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/main Packages                                                             
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/restricted Packages                                                       
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/restricted Sources                                                        
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/main Sources                                                              
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Sources                                                        
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/universe Sources                                                          
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/universe Packages                                                         
  302 Found
Err http://us.archive.ubuntu.com gutsy-updates/multiverse Packages                                                       
  302 Found
Ign http://security.ubuntu.com gutsy-security Release.gpg                                                                
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security Release
Ign http://security.ubuntu.com gutsy-security/restricted Packages
Ign http://security.ubuntu.com gutsy-security/main Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://security.ubuntu.com gutsy-security/universe Packages
Err http://security.ubuntu.com gutsy-security/restricted Packages
  302 Found
Err http://security.ubuntu.com gutsy-security/main Packages
  302 Found
Err http://security.ubuntu.com gutsy-security/multiverse Packages
  302 Found
Err http://security.ubuntu.com gutsy-security/universe Packages
  302 Found
Fetched 380B in 18s (20B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here my /etc/apt/sources.list file in case there's something wrong with this that I can't see:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe

```

Any idea how to fix this?

---

### Post by jdrysdale on 2008-02-24
In software sources try changing the 'Download from' from your local server to main. Worked for me

---

### Post by Levander on 2008-02-24
Yeah, that did something.  My local server is the United States one.  

After changing the "Download From" and you close that dialog, you're prompted to reload your apt indexes.  When I did this, I got a couple of errors on the medibuntu.org repository.  But, then I ran 'sudo apt-get update' from the command line and it worked fine.

Then I went back to the "Software Sources" dialog and changed the "Download From" back to the United States.  I closed the dialog and did the reload when prompted.  This time I got errors on Medibuntu again.  Went to the command line and 'sudo apt-get update' appeared to have run fine.  This last bit kind of makes me think it wasn't the United States server and it's my box. 

I have no idea what happened.  I'll probably end up bumping this thread again because something else will look weird.

Thanks.

---


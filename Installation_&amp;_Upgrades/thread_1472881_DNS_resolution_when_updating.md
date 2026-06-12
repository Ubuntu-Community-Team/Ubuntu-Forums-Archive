---
title: "DNS resolution when updating"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by szlwzl on 2010-05-04
I am experiencing issues when apt-get update'ing etc. The errors are like the following. I was also getting errors with archive.ubuntu.com but do not have those errors handy. I have resolved them by adding the relevant domains/sub-domains to my /etc/hosts but am confused as to why this is required. I am not using a proxy and am using DNS servers from opendns.com. My /etc/apt/sources.list is also below. Any ideas?

```

Get: 2 http://packages.medibuntu.org lucid Release.gpg                                                                      
Get: 3 http://packages.medibuntu.org/ lucid/free Translation-en_GB [2,473B]                                                 
99% [3 Translation-en_GB bzip2 0B] [Connecting to dl.google.com] [Connecting to ppa.launchpad.net] [Connecting to guide.openbzip2: (stdin) is not a bzip2 file.
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                                                             
Get: 4 http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                                      
67% [4 Translation-en_GB bzip2 0B] [Connecting to dl.google.com] [Connecting to ppa.launchpad.net] [Connecting to packages.mbzip2: (stdin) is not a bzip2 file.
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                                         
Get: 5 http://packages.medibuntu.org lucid Release [6,854B]                                                                 
Err http://packages.medibuntu.org lucid Release                                                                             
  
Get: 6 http://ppa.launchpad.net lucid Release.gpg [2,481B]                                                                  
Get: 7 http://ppa.launchpad.net/shiki/mediainfo/ubuntu/ lucid/main Translation-en_GB [2,593B]                               
74% [7 Translation-en_GB bzip2 0B] [Connecting to dl.google.com] [Connecting to guide.opendns.com (208.69.35.136)] [Connectibzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/shiki/mediainfo/ubuntu/ lucid/main Translation-en_GB                                           
Get: 8 http://ppa.launchpad.net lucid Release.gpg                                                                           
Get: 9 http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_GB [2,573B]                                    
69% [9 Translation-en_GB bzip2 0B] [Connecting to dl.google.com] [Connecting to guide.opendns.com (208.69.35.136)] [Connectibzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_GB                                                
Get: 10 http://ppa.launchpad.net lucid Release.gpg                                                                          
Get: 11 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_GB [2,593B]                              
65% [11 Translation-en_GB bzip2 0B] [Connecting to dl.google.com] [Connecting to download.skype.com] [Connecting to deb.operbzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_GB                                           
Hit http://ppa.launchpad.net lucid Release                                                                                  
Err http://ppa.launchpad.net lucid Release                                                                                  
  
Hit http://ppa.launchpad.net lucid Release                                                                                  
Err http://ppa.launchpad.net lucid Release                                                                                  
  
Hit http://ppa.launchpad.net lucid Release                                                                                  
Err http://ppa.launchpad.net lucid Release                                                                                  
  
Err http://dl.google.com stable Release.gpg                                                                                 
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://download.skype.com stable Release.gpg                                                                            
  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)
Err http://deb.opera.com stable Release.gpg                                                                                 
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Ign http://deb.opera.com/opera-beta/ stable/non-free Translation-en_GB                                                      
Hit http://deb.opera.com stable Release                                                                                     
Ign http://deb.opera.com stable/non-free Packages                                                                           
Ign http://deb.opera.com stable/non-free Packages                                                                           
Hit http://deb.opera.com stable/non-free Packages                                                                           
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_GB                                                       
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_GB   
Get: 12 http://dl.google.com stable Release [2,540B]
Get: 13 http://dl.google.com stable/non-free Packages [1,010B]  
Get: 14 http://dl.google.com stable/main Packages [892B]                           
Get: 15 http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_GB [2,601B]
65% [15 Translation-en_GB bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_GB
Ign http://download.skype.com stable Release
Hit http://download.skype.com stable/non-free Packages                                                                      
Fetched 36.6kB in 30s (1,196B/s)                                                                                            
Reading package lists... Done
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://packages.medibuntu.org lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://ppa.launchpad.net lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg  Something wicked happened resolving 'download.skype.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera-beta/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/shiki/mediainfo/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

```

cat /etc/apt/sources.list
#############################################################

################### OFFICIAL UBUNTU REPOS ###################

#############################################################



###### Ubuntu Main Repos

deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse



###### Ubuntu Update Repos

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse



###### Ubuntu Partner Repo

deb http://archive.canonical.com/ubuntu lucid partner

deb-src http://archive.canonical.com/ubuntu lucid partner



##############################################################

##################### UNOFFICIAL  REPOS ######################

##############################################################



###### 3rd Party Binary Repos



#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html

## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -

deb http://dl.google.com/linux/deb/ stable non-free



#### MediaInfo - http://mediainfo.sourceforge.net

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54

deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main



#### Medibuntu - http://www.medibuntu.org/ 

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

deb http://packages.medibuntu.org/ lucid free non-free



#### Skype - http://www.skype.com

## Run this command: gpg --keyserver pgp.mit.edu --recv-keys 0xd66b746e && gpg --export --armor 0xd66b746e  | sudo apt-key add -

deb http://download.skype.com/linux/repos/debian/ stable non-free



#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE

deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main



#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0

deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main





####### 3rd Party Source Repos



#### MediaInfo (Source) - http://mediainfo.sourceforge.net

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54

deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main



#### Medibuntu (Source) - http://www.medibuntu.org/ 

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

deb-src http://packages.medibuntu.org/ lucid free non-free



#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE

deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main



#### Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0

deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main


```

---

### Post by dr_smit on 2010-06-12
Repeatedly, same problem with me too..
Any solution/

---

### Post by dr_smit on 2010-06-12
[http://ubuntuforums.org/showthread.php?t=1475399&page=2](http://ubuntuforums.org/showthread.php?t=1475399&page=2)
similar thread

---

### Post by edochan on 2010-07-10
I had the same problem with my third-party repos on my laptop connecting by wireless.

To work around it for now, I saw it was failing on 
deb.opera.com
...and
dl.google.com

...so I looked up those two hostnames:
nslookup deb.opera.com
nslookup dl.google.com

...and stuck them at the end of my /etc/hosts:
64.233.189.190    dl.google.com
195.189.143.183    deb.opera.com

...after which it worked OK.

---


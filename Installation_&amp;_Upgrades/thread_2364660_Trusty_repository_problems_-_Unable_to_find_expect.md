---
title: "Trusty repository problems - Unable to find expected entry 'restricted/binary-amd64/P"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by jbothma on 2017-06-26
I'm having trouble updating and installing packages in a Trusty image from docker hub. It doesn't look like it's doing anything unusual so I can't tell why it's getting unexpected responses.


 ```
docker run -ti --name trusty-fail ubuntu:trusty-20170620 bash
...
root@e70a33addf23:/# apt-get update -y
...
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
root@e70a33addf23:/# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.3KLcLpoTlK --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: public key "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1

``` 
so far so reasonable


```
root@e70a33addf23:/# apt-get update -y
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [72 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [11.9 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources [1335 kB]                  
Fetched 1347 kB in 7s (176 kB/s)                                               
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
root@e70a33addf23:/# vi /etc/apt/sources.list

``` 
drop main deb-src

```
root@e70a33addf23:/# apt-get update -y
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [72 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [11.9 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources [1335 kB]                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages [1743 kB]           
Fetched 3090 kB in 13s (230 kB/s)                                              
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  Hash Sum mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
root@e70a33addf23:/# vi /etc/apt/sources.list

``` 
drop restricted deb
...
drop universe deb

```
root@e70a33addf23:/# apt-get update -y
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [58.5 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe amd64 Packages          
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages [1743 kB]           
Fetched 1802 kB in 18s (96.0 kB/s)                                             
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

``` 

This is what sources.list looks like

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main
# restricted
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty
# universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security multiverse

```

---


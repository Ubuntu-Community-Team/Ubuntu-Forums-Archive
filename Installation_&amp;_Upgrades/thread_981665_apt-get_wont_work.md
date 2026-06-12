---
title: "apt-get wont work"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Axel-P on 2008-11-13
Hey, 

It hasn't been a long time since I have Ubuntu (8.10) and i get this error message whit apt-get update many times

```
Err http://medibuntu.sos-sts.com free Release.gpg
  Could not resolve 'medibuntu.sos-sts.com'      
Err http://medibuntu.sos-sts.com free/non-free Translation-en_CA
  Could not resolve 'medibuntu.sos-sts.com'                     
Hit http://security.ubuntu.com intrepid-security Release.gpg                                               
Ign http://security.ubuntu.com intrepid-security/main Translation-en_CA                                    
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_CA                              
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_CA                                
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_CA                              
Hit http://security.ubuntu.com intrepid-security Release                                                   
Hit http://security.ubuntu.com intrepid-security/main Packages                                             
Hit http://security.ubuntu.com intrepid-security/restricted Packages                                       
Hit http://security.ubuntu.com intrepid-security/main Sources                                              
Hit http://security.ubuntu.com intrepid-security/restricted Sources                                        
Hit http://security.ubuntu.com intrepid-security/universe Packages                                         
Hit http://security.ubuntu.com intrepid-security/universe Sources                                          
Hit http://security.ubuntu.com intrepid-security/multiverse Packages                                       
Hit http://security.ubuntu.com intrepid-security/multiverse Sources                                        
Hit http://ca.archive.ubuntu.com intrepid Release.gpg                                                      
Ign http://ca.archive.ubuntu.com intrepid/main Translation-en_CA                                           
Hit http://ca.archive.ubuntu.com intrepid/restricted Translation-en_CA                                     
Ign http://ca.archive.ubuntu.com intrepid/universe Translation-en_CA                                       
Ign http://ca.archive.ubuntu.com intrepid/multiverse Translation-en_CA                                     
Hit http://ca.archive.ubuntu.com intrepid-updates Release.gpg                                              
Ign http://ca.archive.ubuntu.com intrepid-updates/main Translation-en_CA                                   
Ign http://ca.archive.ubuntu.com intrepid-updates/restricted Translation-en_CA                             
Ign http://ca.archive.ubuntu.com intrepid-updates/universe Translation-en_CA                               
Ign http://ca.archive.ubuntu.com intrepid-updates/multiverse Translation-en_CA                             
Hit http://ca.archive.ubuntu.com intrepid Release                                                          
Hit http://ca.archive.ubuntu.com intrepid-updates Release                                                  
Hit http://ca.archive.ubuntu.com intrepid/main Packages                                                    
Hit http://ca.archive.ubuntu.com intrepid/restricted Packages                                              
Hit http://ca.archive.ubuntu.com intrepid/main Sources                                                     
Hit http://ca.archive.ubuntu.com intrepid/restricted Sources                                               
Hit http://ca.archive.ubuntu.com intrepid/universe Packages                                                
Hit http://ca.archive.ubuntu.com intrepid/universe Sources
Hit http://ca.archive.ubuntu.com intrepid/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid/multiverse Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/main Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/main Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
W: Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/Release.gpg  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/i18n/Translation-en_CA.bz2  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

I've tried to update from many networks and today 2 updates showed up, but im sure this isn't working. Can someone help me?

---

### Post by inobe on 2008-11-14
make sure synaptic is closed and not running.

open terminal and do

```
sudo apt-get update
```

let us know

---

### Post by kerry_s on 2008-11-14
that medibuntu repo does not look right.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Axel-P on 2008-11-14
Well i did apt-get update and the problem still there, then i went to add (just to be sure) the ubuntu 8.10 repositories and it seems to donwload a little bit more but it still prompts the error at the end.

```
W: Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/Release.gpg  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/i18n/Translation-en_CA.bz2  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

Thanks again

---

### Post by taurus on 2008-11-14
You are running Intrepid but why do you have Feisty repos in your /etc/apt/sources.list?  

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove any line that contains **medibuntu.sos-sts.com**.  Save it and close down gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```
And if you want to install more media codecs, use this guide.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pluckypigeon on 2008-11-14
you need to replace that medibuntu repo with intrepid


```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

type this in a terminal

then this: 
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

then try updating again

---

### Post by pluckypigeon on 2008-11-14
> **taurus said:**
> You are running Intrepid but why do you have Feisty repos in your /etc/apt/sources.list?  

Edit /etc/apt/sources.list




i'm sure medibuntu keeps its repos in /etc/apt/sources.list.d/

Anyway my post above should fix the problem

---

### Post by Axel-P on 2008-11-14
Wow! it worked!
Thanks to everybody!!!

---

### Post by pluckypigeon on 2008-11-14
> **Axel-P said:**
> Wow! it worked!
Thanks to everybody!!!

No problemo but what exactly did you do??

---


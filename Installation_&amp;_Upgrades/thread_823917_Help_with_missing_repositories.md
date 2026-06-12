---
title: "Help with missing repositories"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by PietreWitobi on 2008-06-09
I seem to be unable to link up with certain repositories, help anyone?  Below is a response from my box.

```
$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]         
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                 
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]          
Get:5 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]       
Hit http://us.archive.ubuntu.com gutsy Release                              
Hit http://archive.canonical.com gutsy Release                                 
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://us.archive.ubuntu.com gutsy-backports Release
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Fetched 5B in 0s (6B/s)  
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Where did they go?

---

### Post by Rocket2DMn on 2008-06-09
If they were working before, the chances are that certain areas of the repository are just down for the moment.  Check back in a few hours and see if the problem disappears.

---

### Post by PietreWitobi on 2008-06-09
Mmm... This problem has been persistant.

---

### Post by iaculallad on 2008-06-09
Try:

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by Rocket2DMn on 2008-06-09
You can try switching mirrors by going to System->Administration->Software Sources, this tends to solve 99% of repository problems.

---


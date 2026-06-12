---
title: "Trying to upgrade from 11.04 to 12.04 on ARM CPU"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by SqueeglePoof on 2013-06-12
I'm working on a Beagleboard-xM with Ubuntu 11.04 installed. I tried to compile a program from source and all was going well until I ran into an internal compiler error, which means (I think) that I have to try to upgrade gcc from version 4.5.

So I tried
```
sudo apt-get update
```

and I get
```

Ign http://archive.canonical.com precise InRelease
Hit http://archive.canonical.com precise Release.gpg
Hit http://archive.canonical.com precise Release
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Hit http://archive.canonical.com precise/partner armel Packages
Hit http://us.archive.ubuntu.com precise Release.gpg
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://us.archive.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-security Release             
Hit http://us.archive.ubuntu.com precise-updates Release
Ign http://archive.canonical.com precise/partner Translation-en_US    
Ign http://archive.canonical.com precise/partner Translation-en       
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:1 http://us.archive.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:2 http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:3 http://us.archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:4 http://us.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-security/main Translation-en
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                          
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                    
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                      
Err http://us.archive.ubuntu.com precise/main armel Packages                                                  
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/restricted armel Packages                                            
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/universe armel Packages                                              
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/multiverse armel Packages                                            
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-security/main armel Packages                                         
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-security/restricted armel Packages                                   
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-security/universe armel Packages                                     
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-security/multiverse armel Packages                                   
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/main armel Packages                                          
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/restricted armel Packages                                    
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/universe armel Packages                                      
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/multiverse armel Packages                                    
  404  Not Found [IP: 91.189.91.13 80]
Fetched 290 B in 2min 8s (2 B/s)                                                                              
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-armel/Packages  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

My /etc/apt/sources.list is as follows:
```

deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner

```

Please help.

---

### Post by sanderj on 2013-06-12
Ubuntu 11.04 is not supported anymore (see [https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions) ), so you can't update it anymore using the normal online repo's

---

### Post by SqueeglePoof on 2013-06-13
I tried looking at how to upgrade from Natty from this page: [https://help.ubuntu.com/community/EOLUpgrades/Natty](https://help.ubuntu.com/community/EOLUpgrades/Natty)
which I got from here: [https://help.ubuntu.com/community/UpgradeNotes#Ubuntu_11.04_.28Natty_Narwhal.29](https://help.ubuntu.com/community/UpgradeNotes#Ubuntu_11.04_.28Natty_Narwhal.29)

How, then, do I approach this upgrade? Thanks for the help.

---

### Post by sanderj on 2013-06-13
If those pages do not provide you with the info you need, I would advice you to do a fresh install.

---

### Post by SqueeglePoof on 2013-06-13
I have two options:
[LIST=1]
[*]Find a way to upgrade from 11.04 to a more recent version without doing a fresh install
[*]Backup _everything_ and do a fresh install, then put everything back
[/LIST]

Any advice on either of these options?

---

### Post by gordintoronto on 2013-06-13
Fresh install! You waited too long to decide what to do as 11.04 lost support.

Make two copies of your backup. Don't forget browser bookmarks and such application-specific data.

---


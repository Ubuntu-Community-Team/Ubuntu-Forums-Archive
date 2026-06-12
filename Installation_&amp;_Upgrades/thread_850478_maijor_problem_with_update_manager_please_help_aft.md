---
title: "maijor problem with update manager please help after upgrade"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by antez on 2008-07-05
Hello 

I had a problem with update manage after updateing from gutsy 7.10 to hardy 8.10 

firt I had a debreaper problem, then i think i fixed it but  when i try to update its says: 
    Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



what should i do? i am a new to ubuntu so please help!!!

---

### Post by avtolle on 2008-07-05
You need to get rid of those repositories. First option; go into System>>Administration>>Software Sources, third party tab, and uncheck these; reload and try again.

Second option: from the terminal (Applications>>Accessories>>Terminal) ```
 cp /etc/apt/sources.list /etc/apt/sources.list.bak #make a backup
sudo nano /etc/apt/sources.list #open list for editing
```then either delete the two lines, or comment them out by putting # before each. Then, while still in terminal```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by antez on 2008-07-05
thnx very much for the quick reply man it seems it worked well but i have a question:
now that i desabled them how do i run compiz fusion? (maybe its an idiots question)

---

### Post by avtolle on 2008-07-05
Don't know, don't run it, don't want to run it; I'm sure others will be able to help.

---

### Post by antez on 2008-07-05
thnx

---


---
title: "The Update Manager keeps finding the same problem"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by darthen on 2008-08-26
Everytime the update manager tries to check for updates it seems to get stuck and then it shows me this message

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found [IP: 88.191.250.18 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I am sure my connection is allright so I cant find what is wrong!

---

### Post by vorgusa on 2008-08-26
Did you try to ping something like ping [www.google.com](www.google.com).. This will let you know if DNS and your network settings are correct.. also check that your repository sources are correct

---

### Post by darthen on 2008-08-26
How can I check my repositories? I am a newbie to Linux so I dont know a lot!
thx for the reply anyway!!!!

---

### Post by vorgusa on 2008-08-28
Go to System-> administrator -> Software repositories (I believe that is what it is called) 

look around in there to see if there is anything that stands out.. like nothing being checked.  also check the main repository (I believe that is what it is called, sorry I am not at home with my computer)  and see if your Country is correct.. maybe try another. 

Also did you try pinging?

---


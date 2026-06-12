---
title: "error when trying to update through Update Manager"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by 825522 on 2013-03-13
Hi, when i click the check the button it says. (Failed to download reppository informastion, check your internet connection) and im allwes on the net so it cant be the internet but when i click on Details i get this

```
W:Failed to fetch http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I dont know what to do, please help thanks everyone.:P

---

### Post by ibjsb4 on 2013-03-14
Looks like stormcloud has been deleted from the ppa.

[http://ppa.launchpad.net/cooperjona/](http://ppa.launchpad.net/cooperjona/)

---

### Post by 825522 on 2013-03-14
i dont understand i went to the link but im not sure what link to go to I clicked on stormcloud but it brings me to know where.

---

### Post by ibjsb4 on 2013-03-14
> **825522 said:**
> i dont understand i went to the link but im not sure what link to go to I clicked on stormcloud but it brings me to know where.

Thats because it no longer exist, its been removed.  You can no longer get stormcloud.

---

### Post by 825522 on 2013-03-14
so do i just fuget about that error, Can i still update. Because I dont even know what stormcloud is.

---

### Post by schragge on 2013-03-14
Open a terminal (press **Ctrl**+**Alt**+**t**) and run ```
sudo add-apt-repository -r ppa:cooperjona/stormcloud
```

---

### Post by 825522 on 2013-03-14
This is what Comes up and sorry about this
> Cannot access PPA ([https://launchpad.net/api/1.0/~cooperjona/+archive/stromcloud](https://launchpad.net/api/1.0/~cooperjona/+archive/stromcloud)) to get PPA information, please check your internet connection.

---

### Post by schragge on 2013-03-14
Sorry, there was a typo in the command I posted. Corrected now. Please re-run again.

---

### Post by 825522 on 2013-03-14
So try this one  

> sudo add-apt-repository -r ppa:cooperjona/stormcloud

same thing

> Cannot access PPA  ([https://launchpad.net/api/1.0/~cooperjona/+archive/stormcloud](https://launchpad.net/api/1.0/~cooperjona/+archive/stormcloud)) to get  PPA information, please check your internet connection.

---

### Post by ibjsb4 on 2013-03-14
Should be able to remove it from here.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by 825522 on 2013-03-14
Hi, I get this when trying to run software sources
> Please run this software with adminstrative rights. To do so, run this program with kdesudo

what dose that mean. I am the admin

---

### Post by ibjsb4 on 2013-03-14
Are you running Kubuntu, you listed this thread as Ubuntu.  If this is KDE, in terminal:

```
kdesudo software-properties-kde
```

---

### Post by 825522 on 2013-03-14
Im runing Ubuntu 12.04 LTS Would this work on it

> kdesudo software-properties-kde

---

### Post by ibjsb4 on 2013-03-14
> **825522 said:**
> Im runing Ubuntu 12.04 LTS Would this work on it

Nope, for Ubuntu the command would be:

```
gksudo software-properties-gtk
```

---

### Post by 825522 on 2013-03-14
Ok i did it and now theres no errors and its updateing now thanks everyone for your help I realy appreciate all of your help:p

---

### Post by ibjsb4 on 2013-03-14
Good show :)

One last thing

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


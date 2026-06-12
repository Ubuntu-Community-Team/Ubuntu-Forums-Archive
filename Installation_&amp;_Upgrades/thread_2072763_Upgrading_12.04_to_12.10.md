---
title: "Upgrading 12.04 to 12.10"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by bbno3 on 2012-10-18
My update manager *the default one* dosn't display the new update and the last time i tryed to upgrade i had to enter a terminal command to do so, can anyone help me with what terminal command this is? or how to get my update manager working? The error i get when trying to check for updates is ERROR: No internet*or something like this* W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , W:Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , E:Some index files failed to download. They have been ignored, or old ones used instead. i just want to upgrade to the new one without doing a clean install!

---

### Post by GreenTaurus on 2012-10-18
> **bbno3 said:**
> My update manager *the default one* dosn't display the new update and the last time i tryed to upgrade i had to enter a terminal command to do so, can anyone help me with what terminal command this is? or how to get my update manager working? The error i get when trying to check for updates is ERROR: No internet*or something like this* W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , W:Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , E:Some index files failed to download. They have been ignored, or old ones used instead. i just want to upgrade to the new one without doing a clean install!

sudo apt-get dist-upgrade sound about right?

---

### Post by SlugSlug on 2012-10-18
can you post out put in code tags of 

```
sudo apt-get update
```

and 

```
cat /etc/update-manager/release-upgrades
```

---

### Post by bbno3 on 2012-10-18
> **SlugSlug said:**
> can you post out put in code tags of 

```
sudo apt-get update
```and 

```
cat /etc/update-manager/release-upgrades
```

 W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)  E: Some index files failed to download. They have been ignored, or old ones used instead.  And  # #  never  - Never check for a new release. #  normal - Check to see if a new release is available.  If more than one new #           release is found, the release upgrader will attempt to upgrade to #           the release that immediately succeeds the currently-running #           release. #  lts    - Check to see if a new LTS release is available.  The upgrader #           will attempt to upgrade to the first LTS release available after #           the currently-running one.  Note that this option should not be #           used if the currently-running release is not itself an LTS #           release, since in that case the upgrader won't be able to #           determine if a newer release is available. prompt=normal  and sudo apt-get dist-upgrade dosn't work.

---

### Post by SlugSlug on 2012-10-18
Did you stop an installation mid way through? 

try 

```
sudo do-release-upgrade 
```

---

### Post by JimBuntu on 2012-10-18
My system is not finding the update yet either. Tried doing the terminal codes as well as through update manager. Could it be as simple as it's just not officially out yet?

---

### Post by SlugSlug on 2012-10-18
It is out, but can take 24 hours to sync round all the mirrors.

It's worth checking your 
/etc/update-manager/release-upgrades

file as an LTS (12.04) install will only upgrade to an LTS release. So you would need to edit it should you wish to upgrade to the 12.10.

Me personally after a few years of upgrading have decided to stick to the LTS release's and add PPA's for the apps I use like firebox / Thunderbird and cinnamon

---

### Post by bbno3 on 2012-10-18
> **SlugSlug said:**
> Did you stop an installation mid way through? 

try 

```
sudo do-release-upgrade 
```

 Error during update   A problem occurred during the update. This is usually some sort of  network problem, please check your network connection and retry.   W:Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release  file (Wrong sources.list entry or malformed file)  , W:Failed to fetch  [http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release  file (Wrong sources.list entry or malformed file)  , E:Some index files failed to download. They have been ignored, or  old ones used instead.    Restoring original system state  Aborting Reading package lists... Done     Building dependency tree           Reading state information... Done Building data structures... Done

---

### Post by JimBuntu on 2012-10-18
> **JimBuntu said:**
> My system is not finding the update yet either. Tried doing the terminal codes as well as through update manager. Could it be as simple as it's just not officially out yet?

Just fixed by going to Update Manager>Settings>Updates Tab>Notify me of new Version... Set to Any New Version. Mine, for some reason, was set to LTS Only... 

Right after I changed that Update Manager showed 12.10

---

### Post by SlugSlug on 2012-10-18
> **bbno3 said:**
> Error during update   A problem occurred during the update. This is usually some sort of  network problem, please check your network connection and retry.   W:Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release  file (Wrong sources.list entry or malformed file)  , W:Failed to fetch  [http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release  file (Wrong sources.list entry or malformed file)  , E:Some index files failed to download. They have been ignored, or  old ones used instead.    Restoring original system state  Aborting Reading package lists... Done     Building dependency tree           Reading state information... Done Building data structures... Done


Can you use CODE tags (the little # symbol when you reply)

and post he out put of

```
cat /ect/apt/sources.list
```

---

### Post by bbno3 on 2012-10-18
#cat: /ect/apt/sources.list: No such file or directory

---

### Post by SlugSlug on 2012-10-18
sorry its 
cat /etc/apt/sources.list

and inside [ code] PASTE HERE [ /code]

---

### Post by bbno3 on 2012-10-19
> **SlugSlug said:**
> sorry its 
cat /etc/apt/sources.list

and inside [ code] PASTE HERE [ /code]

 The update manager is working but it shows a new error  ```
 W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/Release  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , W:Failed to fetch http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Slim Odds on 2012-10-19
> **JimBuntu said:**
> Just fixed by going to Update Manager>Settings>Updates Tab>Notify me of new Version... Set to Any New Version. Mine, for some reason, was set to LTS Only... 

Right after I changed that Update Manager showed 12.10
The default for LTS releases is to only look for another LTS release.

This default makes good sense and can be easily changed as you've seen.

---

### Post by SlugSlug on 2012-10-20
> **bbno3 said:**
> The update manager is working but it shows a new error  ```
 W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/Release  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , W:Failed to fetch http://gg.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file) , E:Some index files failed to download. They have been ignored, or old ones used instead.
```


You have a bad entry in 
  
/etc/apt/sources.list

It's the one its showing.

if you post 

```
 cat /etc/apt/sources.list
```

in code tags we could fix it

---

### Post by crave-n on 2012-10-20
i also suffer from the same problem can any one help :(
i've already set the notify me for new version as "for any new version"
but still update manager doesnt recognise any new releases

---

### Post by bbno3 on 2012-10-20
> **SlugSlug said:**
> You have a bad entry in 
  
/etc/apt/sources.list

It's the one its showing.

if you post 

```
 cat /etc/apt/sources.list
```in code tags we could fix it

 ```
 brandon@Ghost-DT1404:~$ cat /etc/apt/sources.list # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/  # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to # newer versions of the distribution. deb http://gg.archive.ubuntu.com/ubuntu/ quantal main restricted deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal main restricted  ## Major bug fix updates produced after the final release of the ## distribution. deb http://gg.archive.ubuntu.com/ubuntu/ quantal-updates main restricted deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal-updates main restricted  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb http://gg.archive.ubuntu.com/ubuntu/ quantal universe deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal universe deb http://gg.archive.ubuntu.com/ubuntu/ quantal-updates universe deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb http://gg.archive.ubuntu.com/ubuntu/ quantal multiverse deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal multiverse deb http://gg.archive.ubuntu.com/ubuntu/ quantal-updates multiverse deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal-updates multiverse  ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. deb http://gg.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse independent deb-src http://gg.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse independent  deb http://security.ubuntu.com/ubuntu quantal-security main restricted independent deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted independent deb http://security.ubuntu.com/ubuntu quantal-security universe deb-src http://security.ubuntu.com/ubuntu quantal-security universe deb http://security.ubuntu.com/ubuntu quantal-security multiverse deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. # deb http://archive.canonical.com/ubuntu oneiric partner # deb-src http://archive.canonical.com/ubuntu oneiric partner  ## This software is not part of Ubuntu, but is offered by third-party ## developers who want to ship their latest software. deb http://extras.ubuntu.com/ubuntu quantal main deb-src http://extras.ubuntu.com/ubuntu quantal main brandon@Ghost-DT1404:~$  
```

---


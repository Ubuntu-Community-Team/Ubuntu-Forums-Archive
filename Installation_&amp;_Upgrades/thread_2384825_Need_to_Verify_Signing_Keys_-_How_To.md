---
title: "Need to Verify Signing Keys - How To"
date: 2018-02-12
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2018-02-12
Curious and need to know ... Are UbuntuStudio signing keys the same as Ubuntu? Or Xubuntu?

Need to verify that a friend has the correct signing keys before doing updates. How can we do this in v16.04?
I ran the following - and even though I running UbuntuStudio it shows Ubuntu. Makes me question - is this normal?
He has Xubuntu. So how can a person find out???

```

lsb_release -d
Description:    Ubuntu 16.04.3 LTS

```

Thanks!

---

### Post by Rick St. George on 2018-02-13
Noticed a recent update for Software Updater when running a recent update. Now I get this ...

"failed to download repository information" in UbuntuStudio v16.04. After looking at the Tabs, everything seems OK. Close it and then it shows "Software on this computer is up to date". What ?!?!?!?  Here is a print of code I ran.

```

~$ cat /etc/apt/sources.list

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted

###### VirtualBox Repo
deb http://download.virtualbox.org/virtualbox/debian xenial contrib

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
# deb-src http://deb.opera.com/opera-stable/ stable non-free
deb http://archive.ubuntustudio.org/ubuntustudio xenial main


~$ ls /etc/apt/sources.list.d/
kdenlive-ubuntu-kdenlive-stable-xenial.list
kdenlive-ubuntu-kdenlive-stable-xenial.list.save
opera.list
opera.list.save
opera-stable.list
opera-stable.list.distUpgrade
opera-stable.list.save
team-xbmc-ubuntu-ppa-xenial.list
team-xbmc-ubuntu-ppa-xenial.list.save
virtualbox.list
virtualbox.list.distUpgrade
virtualbox.list.save
stephen@stephen-evo-5723:~$ 


```

Nothing seems out of place!  What do you think?

Thanks!
Rick

---

### Post by QIII on 2018-02-13
Could you post the results of

```
sudo apt update
```

so we can see if there might be more detailed clues there?

---

### Post by #&amp;thj^% on 2018-02-13
Will you show us the error with:
```
sudo apt update
```
HA! Ninja'ed by QIII

---

### Post by Rick St. George on 2018-02-13
Ahhh !!!

```

~$ sudo apt update
 
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Hit:3 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]      
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]       
Hit:6 http://deb.opera.com/opera-stable stable InRelease                       
Err:7 http://archive.ubuntustudio.org/ubuntustudio xenial InRelease            
  Could not resolve 'archive.ubuntustudio.org'
Fetched 204 kB in 1s (132 kB/s)                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/xenial/InRelease  Could not resolve 'archive.ubuntustudio.org'
W: Some index files failed to download. They have been ignored, or old ones used instead.


```

Now ... What to do about it?

---

### Post by #&amp;thj^% on 2018-02-13
> **Rick St. George said:**
> Ahhh !!!

Now ... What to do about it?
Fade 3 and Punt! :D (Joke)
Lets see how this Looks:
```
nano /etc/resolv.conf
```
Paste back please. This could be a cumbersome process so don't get frustrated.;)

---

### Post by QIII on 2018-02-13
archive.ubuntustudio.org does not appear to exist.

How did that come to be in your sources list?

---

### Post by Rick St. George on 2018-02-13
> **1fallen said:**
> Fade 3 and Punt! :D (Joke)
Lets see how this Looks:
```
nano /etc/resolv.conf
```
Paste back please. This could be a cumbersome process so don't get frustrated.;)

That has my comcast access route and 
nameserver 127.0.1.1

---

### Post by Rick St. George on 2018-02-13
> **QIII said:**
> archive.ubuntustudio.org does not appear to exist.

How did that come to be in your sources list?

I suppose it should be there ... I'm running UbuntuStudio v16.04 I thought!?!

---

### Post by #&amp;thj^% on 2018-02-13
> **Rick St. George said:**
> That has my comcast access route and 
nameserver 127.0.1.1

Allrighty then.
And I have you tried switching to another or main server for your sources? [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by tinylagarto on 2018-02-13
I run Xubuntu and have also Ubuntu as release name. That is normal because every community based spin is built on top of the Ubuntu infrastructure. 

What is exactly you want to achieve?

---

### Post by deadflowr on 2018-02-13
> Are UbuntuStudio signing keys the same as Ubuntu? Or Xubuntu?
Yes
to see the keys run
```
apt-key list
```

More here probably:
[https://help.ubuntu.com/community/SecureApt]("https://help.ubuntu.com/community/SecureApt")

---

### Post by deadflowr on 2018-02-13
I find it odd you have no universe repository.
(also known as Community)
Odd since UbuntuStudio would be loaded full of community-based packages.

---

### Post by #&amp;thj^% on 2018-02-13
> **deadflowr said:**
> I find it odd you have no universe repository.
(also known as Community)
Odd since UbuntuStudio would be loaded full of community-based packages.

+1
And I just installed Ubuntu Studio and I see no "deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) xenial main"
Stock Repos are:
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
```
So I don't know how to advise, other than disabling the "deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) xenial main"

---

### Post by Rick St. George on 2018-02-13
[QUOTE=1fallen;13739576]Allrighty then.
And I have you tried switching to another or main server for your sources?/QUOTE]

No .. but did just now to U.S.  (I thought main was US)
 Thanks

---

### Post by Rick St. George on 2018-02-13
> **1fallen said:**
> 
And I just installed Ubuntu Studio and I see no "deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) xenial main"
So I don't know how to advise, other than disabling the "deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) xenial main"


Thanks .. I removed it and the annoying reading does not show up.

But I'm wondering ... What are the signing keys for UbuntuStudio? Shouldn't it be different than Ubuntu? What about Xubuntu, etc.?
Perhaps I should say UbuntuStudio Desktop, as that is probably the ONLY difference. But I don't see that either! Is it needed?

Just would like to tidy everything up before jumping upto 17.04.

Thanks!

---

### Post by deadflowr on 2018-02-13
> But I'm wondering ... What are the signing keys for UbuntuStudio? Shouldn't it be different than Ubuntu? What about Xubuntu, etc.?
I posted in the other thread you have: [https://ubuntuforums.org/showthread.php?t=2384825]("https://ubuntuforums.org/showthread.php?t=2384825")
To elaborate, Ubuntu and UbuntuStudio (and every other Official flavor of Ubuntu; ie Xubuntu Kubuntu Lubuntu ,etc etc) all use the same repositories, so they all use the same signing keys.

---

### Post by wildmanne39 on 2018-02-13
Threads merged. Please do not post duplicates, it dilutes community effort.

---

### Post by Rick St. George on 2018-02-14
> **deadflowr said:**
> I posted in the other thread you have: [https://ubuntuforums.org/showthread.php?t=2384825](https://ubuntuforums.org/showthread.php?t=2384825)
To elaborate, Ubuntu and UbuntuStudio (and every other Official flavor of Ubuntu; ie Xubuntu Kubuntu Lubuntu ,etc etc) all use the same repositories, so they all use the same signing keys.

Sorry! This thread kind of morphed into a previous, and was merged ... Good.  But here lies proof of the problem I have. Noticed I don't have UbuntuStudio Publishing. So, in Synaptic Mgr, I selected it and now shows the following.

> 
An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595Failed to fetch [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/dists/xenial/InRelease)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595Some index files failed to download. They have been ignored, or old ones used instead.


Any suggestions of how to get the PPA or whatever I need for these? More likely in the UbuntuStudio-Meta Pkg. This Link may help [https://wiki.ubuntu.com/UbuntuStudio/UbuntuStudioPackages](https://wiki.ubuntu.com/UbuntuStudio/UbuntuStudioPackages) 
Thanks!

---

### Post by deadflowr on 2018-02-14
> Any suggestions of how to get the PPA or whatever I need for these? More likely in the UbuntuStudio-Meta Pkg. This Link may help [https://wiki.ubuntu.com/UbuntuStudio...StudioPackages](https://wiki.ubuntu.com/UbuntuStudio...StudioPackages) 
Thanks!

Yes.
Enable Universe.
No need to add any ppa.
All UbuntuStudio packages are in Ubuntu regular repositories.
But you need the universe repository to get them.

I'm not sure which name UbuntuStudio would use, but open up either "Software and Updates" or something like "Software Sources"
And then make sure there is a check mark for Community (universe).
Then on close you need to let it reload and all UbuntuStudios packages will be available.

Only Ubuntu (out of all the flavors) has all it's default packages in main, as only Ubuntu is fully supported by Canonical.
all other flavors are Community flavors and so they all contain packages from the Community repos.


Hope that make sense.

---

### Post by Rick St. George on 2018-02-14
Thanks "deadflowr". This is what I have now ...

```

$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease            
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:5 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu xenial InRelease
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:7 http://deb.opera.com/opera-stable stable InRelease                       
Hit:8 http://archive.canonical.com xenial InRelease                            
Hit:9 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease 
Hit:10 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease
Hit:11 http://ppa.launchpad.net/thomas-schiex/blender/ubuntu xenial InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
33 packages can be upgraded. Run 'apt list --upgradable' to see them.


~$ apt list --upgradable
Listing... Done
apt/xenial-updates 1.2.25 amd64 [upgradable from: 1.2.24]
apt-transport-https/xenial-updates 1.2.25 amd64 [upgradable from: 1.2.24]
apt-utils/xenial-updates 1.2.25 amd64 [upgradable from: 1.2.24]
bsdutils/xenial-updates 1:2.27.1-6ubuntu3.4 amd64 [upgradable from: 1:2.27.1-6ubuntu3.3]
libapt-inst2.0/xenial-updates 1.2.25 amd64 [upgradable from: 1.2.24]
libapt-pkg5.0/xenial-updates 1.2.25 amd64 [upgradable from: 1.2.24]
libblkid1/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
libegl1-mesa/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libfdisk1/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
libgbm1/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libgl1-mesa-dri/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libgl1-mesa-glx/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libglapi-mesa/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libgles2-mesa/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libmount1/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
libosmesa6/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libsmartcols1/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
libuuid1/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
libwayland-egl1-mesa/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
libxatracker2/xenial-updates 17.2.8-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
linux-firmware/xenial-security,xenial-security,xenial-updates,xenial-updates 1.157.16 all [upgradable from: 1.157.15]
mesa-vdpau-drivers/xenial-updates 17.2.8-0ubuntu0~16.04.1 i386 [upgradable from: 17.2.4-0ubuntu1~16.04.4]
mount/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
util-linux/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]
uuid-runtime/xenial-updates 2.27.1-6ubuntu3.4 amd64 [upgradable from: 2.27.1-6ubuntu3.3]

```

Then ran Update. All seems fine. Consider this Case Closed. 
Thanks for the help and patience in teaching me.
Peace,
Rick

---


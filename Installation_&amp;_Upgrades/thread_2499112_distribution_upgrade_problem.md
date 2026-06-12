---
title: "distribution upgrade problem"
date: 2024-07-12
forum: Installation &amp; Upgrades
---

### Post by wish1989 on 2024-07-12
Every time I try to do distribution upgrade I get error as following:

Get:1 [https://apt.repos.intel.com/mkl](https://apt.repos.intel.com/mkl) all InRelease [4,438 B]                  
Get:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) lunar InRelease [48.8 kB]       
Err [https://apt.repos.intel.com/mkl](https://apt.repos.intel.com/mkl) all InRelease                              
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BAC6F0C353D04109
Hit [https://apt.repos.intel.com/oneapi](https://apt.repos.intel.com/oneapi) all InRelease                           
Fetched 53.3 kB in 0s (0 B/s)                                                  

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 


Restoring original system state


Can someone help and suggest how to resolve? Thanks.

---

### Post by oldfred on 2024-07-12
Lunar Lobster 23.04
Ubuntu 23.04 support ends January 25, 2024 

Generally best to just use the LTS versions and update every 2 years.
Install 24.04 after testing live installer & restore your data, list of installed apps and anything else you backup into new install.

I also prefer to do a new clean install & restore data from backup and/or old install as I keep at least two / (root) partitions. One previous LTS and one new/current. And keep all data in separate data partition(s) that I mount in every install.

---

### Post by TheFu on 2024-07-13
Just to be clear, _lunar_ support ended 6 months ago, so the repos are gone.

Stay on supported releases, preferably LTS releases, if you can't be bothered to upgrade every 6 months, or if you are running anything production on the system.

---

### Post by guiverc on 2024-07-13
Ubuntu 23.04 release reached end of life as others have said some time ago...  Refer [https://fridge.ubuntu.com/2024/01/26/ubuntu-23-04-lunar-lobster-reached-end-of-life-on-january-25-2024/](https://fridge.ubuntu.com/2024/01/26/ubuntu-23-04-lunar-lobster-reached-end-of-life-on-january-25-2024/)

For EOLupgrades you can get details from [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Technically a *release-upgrade* can be made until the next release you would normally *release-upgrade* to is supported, as Ubuntu 23.04 would *release-upgrade* to 23.10, you had until 23.10 reached EOL on 11 July 2024...

However, due to some packages that were still in queues for *mantic* or 23.10, the Ubuntu 23.10 release is still technically *supported*, as the process of closure would cause everything in queues to be *dropped* or lost...   Thus for now (*and what could be a number of hours*) the *release-upgrade* from 23.04 to 23.10 is still possible..

The file the upgrade process checks is [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)  which if you scan near the bottom, you'll still see a "Supported: 1" against 23.10/*mantic*; once that is changed you're too late.

If you hurry, you maybe able to beat the closure of 23.10, and *release-upgrade* to 23.10... then you'll be able to *release-upgrade* a second time and get to a *supported* system (or 24.04 LTS).

---

### Post by wish1989 on 2024-07-13
Thank you all for your replies. The problem is when I try to update using system software updater it always shows me "Failed to download repository information. Check your internet connection" but my connection is all fine and I have even tried using different servers and it always has this error. When I try to do upgrade using terminal it always fails mentioning the Intel mkl release line which is in the original post. 

I have 24.04 on a usb I am wondering if I can use that directly to install but I am worried I will lose my dual boot and saved files, would be really helpful if there is some tutorial on it. I apologise maybe they are little bit stupid questions, I am using Ubuntu for not so long so I don't want to risk breaking the system altogether

---

### Post by TheFu on 2024-07-13
You seem to be missing the key point.  The repos you want to use are GONE.

The release you are trying to update has been out of support for months.  There is no "approved" fix other than to install a fresh, supported, release.  Other options ARE possible as guiverc listed.

Asking about some random USB with the contents unclear isn't useful.  We don't know what you man or what is on that USB.  If it is a 24.04 ISO from an ubuntu.com site or other reputable mirror, that's one thing. If it is anything else, who knows?

I cannot help with any dual boot questions. Haven't done that in a very, very, very  long time. Someone else might help, but they will need exact, correct, information, not vague statements. Sorry.

---

### Post by wish1989 on 2024-07-13
Ah okay I get it. Thank you. Yes the usb I have is a 24.04 iso from the ubuntu site directly. I downloaded the iso from the ubuntu website and then used a tool called rufus to write on the usb. Apologies for the vague statements.

---

### Post by TheFu on 2024-07-13
For any files you don't want to lose, make at least 1 backup and validate that you can restore it with whatever is needed to make it useful.  That may just be the data, but it might also include the owner, group, permissions, ACLs and xattrrs, so it is usually best to ensure all of that data is part of the backups you make.

---


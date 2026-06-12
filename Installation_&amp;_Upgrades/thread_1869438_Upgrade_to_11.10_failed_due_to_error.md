---
title: "Upgrade to 11.10 failed due to error"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by willdogs4286 on 2011-10-25
When I try to upgrade to 11.10 I get the following error message:

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release](http://archive.canonical.com/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Could someone please help me out? Go step-by-step cause I'm still pretty new to Linux and haven't yet figured everything out.

---

### Post by critin on 2011-10-25
Did you try to upgrade through the Update Manager?
I don't understand why this page is linked here.  Perhaps the  'main/source/Sources isn't up-to-date in the manager?

Which version are you using now, 11.04?

---

### Post by willdogs4286 on 2011-10-25
I am using 11.04 currently. I tried the update through the update manager as well as through the terminal sudo apt-get upgrade. I get the same message.

---

### Post by Old_Grey_Wolf on 2011-10-25
> **willdogs4286 said:**
> When I try to upgrade to 11.10 I get the following error message:

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release](http://archive.canonical.com/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Could someone please help me out? Go step-by-step cause I'm still pretty new to Linux and haven't yet figured everything out.

It looks like the repo being used is for partner repositories; however, the sources.list is looking for the main repositories. Please post the output of this command entered into the terminal ```
cat /etc/apt/sources.list
```
Then maybe someone can sort the problem.

---

### Post by willdogs4286 on 2011-10-25
Here is what I get:

deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty main
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty main

---

### Post by Old_Grey_Wolf on 2011-10-25
> **willdogs4286 said:**
> I am using 11.04 currently. I tried the update through the update manager as well as through the terminal sudo apt-get upgrade. I get the same message.

Did the **update** manager show the option to **upgrade** to 11.10 at the top of the window? If so, did you select that option?

Edit: also the commands "apt-get upgrade" and "apt-get dist-upgrade" do not install the newest release. There is a different command for that; however, I don't want to tell you what it is until this problem is sorted. Using that command could make solving the problem even more difficult.

---

### Post by critin on 2011-10-25
Is your disk large enough to handle a second os?  If so, I'd personally install on another partition and dual boot for awhile.  Read the forums, there are lots of issues with certain system configurations.  A dual boot will give you a chance to find issues without losing your good set-up.  Be cautious.

---

### Post by willdogs4286 on 2011-10-25
> **critin said:**
> Is your disk large enough to handle a second os?  If so, I'd personally install on another partition and dual boot for awhile.  Read the forums, there are lots of issues with certain system configurations.  A dual boot will give you a chance to find issues without losing your good set-up.  Be cautious.

My system may be big enough but doesn't leave me much hard drive space for anything else without having to try to run programs from my external. This computer is pretty old.

---

### Post by willdogs4286 on 2011-10-25
> **Old_Gray_Wolf said:**
> Did the **update** manager show the option to **upgrade** to 11.10 at the top of the window? If so, did you select that option?

Edit: also the commands "apt-get upgrade" and "apt-get dist-upgrade" do not install the newest release. There is a different command for that; however, I don't want to tell you what it is until this problem is sorted. Using that command could make solving the problem even more difficult.

That was the message I received after trying to upgrade from the update manager.

---

### Post by critin on 2011-10-25
The reason I suggested dual booting is because a lot of users are reporting problems with this release, and wish they hadn't upgraded, especially users who aren't too familiar with ubuntu.  It looks pretty on the outside, but it isn't quite finished inside.  11.04 has been around longer and has many of the bugs fixed already.  

Just because it's on the upDATE manager doesn't mean you should upGRADE to it.  It is not an upDATE.  Just be sure before you do.  None of my business though, forgive me.  Using and fixing things is the best way to learn.  That's what I do and I like to do it that way.   But I keep one or two reliable versions to hold my work and files.

---

### Post by Old_Grey_Wolf on 2011-10-26
> **willdogs4286 said:**
> My system may be big enough but doesn't leave me much hard drive space for anything else without having to try to run programs from my external. This computer is pretty old.

Can you backup your important data before doing the upgrade? I would copy the entire /home directory, including hidden files, to an external drive. **I would highly recommend doing so.**

Once you have your backup of important data; then, you could try to use the command line to upgrade.

First, you need the command line upgrade package. To install it type this command in the terminal ```
sudo apt-get install update-manager-core
``` It is possible that it will tell you that it is already installed.

Then, perform the upgrade to 11.10 using this command ```
sudo do-release-upgrade
```

Then, hope for the best :)

Upgrades have always been hit or miss for me. I usually prepare for a complete re-install when I upgrade just in case something goes wrong. You did say your computer was old; therefore, I suspect that you may have problems with 11.10.

---

### Post by willdogs4286 on 2011-11-01
I am now wondering if I should even upgrade or not now? This computer is about 5 years old and only has about 20 GB of hard drive space total. 

I only ask if I should upgrade, because most of the problems that I have read by users is usually derived from running alongside Windows. I installed 11.04 in place of Windows Vista and it has made my computer seem brand new again. I am wanting to upgrade because I know that as upgrades happen, so too does ease of use.

Please tell me of some of the problems I could face if I upgrade to 11.10. Thanks.

---

### Post by willdogs4286 on 2011-11-09
> **Old_Gray_Wolf said:**
> Can you backup your important data before doing the upgrade? I would copy the entire /home directory, including hidden files, to an external drive. **I would highly recommend doing so.**

Once you have your backup of important data; then, you could try to use the command line to upgrade.

First, you need the command line upgrade package. To install it type this command in the terminal ```
sudo apt-get install update-manager-core
``` It is possible that it will tell you that it is already installed.

Then, perform the upgrade to 11.10 using this command ```
sudo do-release-upgrade
```

Then, hope for the best :)

Upgrades have always been hit or miss for me. I usually prepare for a complete re-install when I upgrade just in case something goes wrong. You did say your computer was old; therefore, I suspect that you may have problems with 11.10.
I tried this and this is what happened in the middle of the upgrade:

"Updating repository information
"WARNING: Failed to read mirror file

"Third party sources disabled 

"Some third party entries in your sources.list were disabled. You can 
"re-enable them after the upgrade with the 'software-properties' tool 
"or your package manager. 

At the end, I got this message:

*Fetched 0 B in 0s (0 B/s)                                                      

*Error during update 

*A problem occurred during the update. This is usually some sort of 
*network problem, please check your network connection and retry. 

*W:Failed to fetch 
*[http://archive.canonical.com/ubuntu/dists/oneiric/Release](http://archive.canonical.com/ubuntu/dists/oneiric/Release) Unable to 
*find expected entry 'main/source/Sources' in Release file (Wrong 
*sources.list entry or malformed file) 
*, E:Some index files failed to download. They have been ignored, or 
*old ones used instead. 


*Restoring original system state

*Aborting
*Reading package lists... Done    
*Building dependency tree          
*Reading state information... Done
*Building data structures... Done

---


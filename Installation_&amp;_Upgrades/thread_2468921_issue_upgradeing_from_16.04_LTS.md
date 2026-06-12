---
title: "issue upgradeing from 16.04 LTS"
date: 2021-11-14
forum: Installation &amp; Upgrades
---

### Post by edstevens on 2021-11-14
On my personal laptop, am running 16.04 LTS and looking to upgrade to 18.04 LTS (and eventually to 20).  Running with Cinnamon desktop.

using simple instructions here ([https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction)), the 'sudo apt update returns several warnings and errors:


```
ed@ed-Gazelle-00:~$ sudo apt update
[sudo] password for ed: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:5 https://repo.skype.com/deb stable InRelease [4,501 B]                    
Hit:6 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease         
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]  
Hit:8 http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu xenial InRelease
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [1,648 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [1,159 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [380 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [93.7 kB]
Err:5 https://repo.skype.com/deb stable InRelease                              
  The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [111 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [9,824 B]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [9,800 B]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,152 B]
Ign:17 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Hit:18 http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial InRelease
Get:19 https://esm.ubuntu.com/infra/ubuntu xenial-infra-security InRelease [7,515 B]
Get:20 https://esm.ubuntu.com/infra/ubuntu xenial-infra-updates InRelease [7,475 B]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [327 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [785 kB]
Hit:23 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Get:24 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [665 kB]
Get:25 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [225 kB]
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [130 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [281 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,960 B]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:30 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [6,608 B]
Hit:31 http://ppa.launchpad.net/x2go/stable/ubuntu xenial InRelease            
Get:32 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [206 kB]
Get:33 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [7,864 B]
Get:34 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [8,084 B]
Get:35 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [2,672 B]
Get:36 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:37 http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [2,638 B]
Ign:17 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Err:17 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.39 80]
Fetched 1,194 kB in 1s (829 kB/s)                                              
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://repo.skype.com/deb stable InRelease: The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
W: Failed to fetch https://repo.skype.com/deb/dists/stable/InRelease  The following signatures were invalid: KEYEXPIRED 1624268195  KEYEXPIRED 1624268195  KEYEXPIRED 1624268195
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/dep11/Components-amd64.yml  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.39 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.

```


Alternately, taking instructions from here: ([https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)), it stated:

[h=2]Upgrading from Ubuntu 16.04 LTS or 17.10[/h] [INDENT][/INDENT]
To upgrade on a desktop system: 
[INDENT]Open the "Software & Updates" Setting in System Settings.[/INDENT]

But when I opened the System Settings, there was no 'Software & Updates' . . .

---

### Post by TheFu on 2021-11-14
If the goal is to get to 20.04, it is time to backup everything you don't want to lose and do a clean install.  Taking cruft forward from 16.04 (and earlier) will create a very odd system, so you'll not be able to follow some of the how-to guides for some of the subsystems.

> &#8220;I say we take off and nuke the entire site from orbit. It&#8217;s the only way to be sure.&#8221;

Migrations up take far too long. Did a few 16.04 --> 18.04 upgrades last year.  A fresh install is 15 minutes.  If you have good backups and save off a list of manually installed packages, your data and your settings, then put those back early on the new install, it is fairly painless to migrate ... using a wiped and fresh installation.  The **apt-mark** command has an option to output the list of manually installed packages. Those can be fed back on the fresh install. Let the package manager handle the hard parts for us.

I've migrated a 16.04 (32-bit) to a 20.04 (64-bit) using that method. Worked well. Took about 45 minutes.

---

### Post by MAFoElffen on 2021-11-14
He could do a migration to get to 18.04 or beyond... But on his problem in how he was trying to get there...

First... Everyone "should" note that he has PPA's that he should disable before trying to go to 18.04. That is where most of his problems are...

If you disable the x2go, webupd8team, and Skype PPA's, (and any other PPA's) then do you still have errors?

---

### Post by TheFu on 2021-11-14
First, ensure all the 16.04 **full-upgrade** apt works.
Next, use **sudo do-release-upgrade** <--- that will remove all the PPAs.
But really, if the goal is to get to 20.04 from 16.04, it will be much quicker to nuke it from orbit and restore your data and settings on the fresh 20.04 system. Just be certain you backup anything you don't want to lose in a way that it can be restored on a 20.04 system.  There are at least 50 threads here about backups and 25 about restores.

---

### Post by grahammechanical on 2021-11-14
You have a repository for Skype. You should remove that repository. I do not think that a Ubuntu upgrade can upgrade Skype. It is also advisable to deactivate any PPAs.

Look for Software and Updates. It is not accessed through System Settings. It is a utility all on its own. Ubuntu 16.04 is so long ago that I cannot direct you how to find it. And certainly not in the Cinnamon user interface. Log into the Ubuntu Gnome user interface.

Regards

---

### Post by MAFoElffen on 2021-11-14
The Skype PPA release key is the one that is expired. That would prevent him using apt until that is disabled. 

I go back on what I said about doing a do-release-upgrade... Usually I would say go for it and see what happens. But I just noticed some other things.

You are right "theFu"... A Migration for him, is probably a much better, far more elegant solution. For some reason, his system has a strange mixture of amd64, i386, and "backports" repo packages...

16.04 to 18.04 were major changes between. Python2 to Python3. Init frameworks to systemd. Big networking changes. Phasing out of i386 packages, besides dropping support for most 32 bit altogether. I'm not sure that these are going to translate well with do release  upgrade solutions. Especially since 16.04 is so far from being current.  Some of those may have deadened. There is lot of what is in your apt update output that looks like a risk in a do-release-upgrade.

Seeing such a mix of arches, ppa's, backports, and (just generally) all kinds of repo "types"... I think I was hasty in recommending that, and have to safely go with TheFu's earlier recommendation on Migrating to 20.04 with a clean install. That would clean all that up and simplify going on from here.

---

### Post by edstevens on 2021-12-03
I apologize for appearing to have abandoned this thread.  Got pulled off on other, unrelated issues and also had to give some consideration about step-wise upgrade vs. nuke it and fresh install of 20.04.  If I decide to go for a fresh install of 20.04, where do you recommend I obtain a copy?  Where do you recommend I go for good, concise instructions?  Google led me first to [https://help.ubuntu.com/lts/installation-guide/](https://help.ubuntu.com/lts/installation-guide/), which then seemed to run to dead-ends or rabbit holes in simply trying to locate a download image to put on a dvd or thumb-drive.

Keep in mind that this is for a personal laptop, not a server.  Most pages I landed on talked about 'ubuntu server'.

---

### Post by Impavidus on 2021-12-04
> **edstevens said:**
>  If I decide to go for a fresh install of 20.04, where do you recommend I obtain a copy?
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
For other flavours, torrent downloads etc., see the links on that site.

---

### Post by edstevens on 2021-12-04
> **Impavidus said:**
> [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
For other flavours, torrent downloads etc., see the links on that site.

Thank you. Got it.  Should be good to go now.

---


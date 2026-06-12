---
title: "no package upgrades for a while"
date: 2019-03-07
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2019-03-07
i have been getting no package upgrades for a while.  i can believe nothing got changed for maybe a week.  but this has been like 3 weeks.  i'm thinking maybe my sources.list got fubarred.  i include it below with line numbers added for reference:

```

lt2a/forums /home/forums 1> cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 16.04.5 LTS _Xenial Xerus_ - Release amd64 (20180731)]/ xenial main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
    16    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    18    
    19    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    20    ## team, and may not be under a free licence. Please satisfy yourself as to 
    21    ## your rights to use the software. Also, please note that software in 
    22    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    23    ## security team.
    24    deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    25    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    26    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    27    
    28    ## N.B. software from this repository may not have been tested as
    29    ## extensively as that contained in the main release, although it includes
    30    ## newer versions of some applications which may provide useful features.
    31    ## Also, please note that software in backports WILL NOT receive any review
    32    ## or updates from the Ubuntu security team.
    33    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    34    
    35    ## Uncomment the following two lines to add software from Canonical's
    36    ## 'partner' repository.
    37    ## This software is not part of Ubuntu, but is offered by Canonical and the
    38    ## respective vendors as a service to Ubuntu users.
    39    deb http://archive.canonical.com/ubuntu xenial partner
    40    deb-src http://archive.canonical.com/ubuntu xenial partner
    41    
    42    deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    44    deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
lt2a/forums /home/forums 2>
```

---

### Post by Skaperen on 2019-03-07
this is my bad.  long ago when i had gotten word of the change to 5 year LTS support i didn't get the info that it only applied to the server edition.  so now i need to go to 18.04 which will be a full fresh install because i need to resize my partitions (my sda1 is too small).  now i need to decide whether i should go with 24GB or 32GB.  i will be installing Xubuntu this time.

---

### Post by deadflowr on 2019-03-07
Ubuntu 16.04 gets 5 years, the server and desktop versions.
The flavors (ie Xubuntu, Kubuntu, etc) almost all only get 3 years of desktop support.
But Ubuntu is a full 5 years for all Ubuntu.

That said, the sources.list only gives us the sources.list to go by.
Perhaps run an apt update apt upgrade and post what that says.

---

### Post by Skaperen on 2019-03-07
i have a script that does apt-get update then apt-get -y upgrade and it runs itself under my logcmd command to record logs.  i just now re-ran it again:

```
Script started on Thu 07 Mar 2019 02:16:05 PM EST
14:16:05 [16269] EXECUTING: '/root/cmd/upgrade'
---------------------------------------------------------------------------------------------------------------------------------------------------------------------update-
2019-03-07-14:16:05.549466133 EXECUTING: apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                      
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                                      
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Reading package lists... Done
[[ real 2.365 - user 1.242 - sys 0.228 - 62.15 ]]
--------------------------------------------------------------------------------------------------------------------------------------------------------------------upgrade-
2019-03-07-14:16:07.951649427 EXECUTING: apt-get -y upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[[ real 0.440 - user 0.422 - sys 0.018 - 100.04 ]]
[[ real 2.883 - user 1.733 - sys 0.255 - 68.96 ]]
14:16:08 [16269] FINISHED - status = 0

Script done on Thu 07 Mar 2019 02:16:09 PM EST
```

just one run alone getting 0 upgraded is not uncommon.  what has been happening is weeks of this, continuously.

---

### Post by Skaperen on 2019-03-07
> **deadflowr said:**
> ...
The flavors (ie Xubuntu, Kubuntu, etc) almost all only get 3 years of desktop support.
...

aren't those just differing by which packages are selected to be installed?  Xubuntu installs packages out of the same repository, just different packages.  what level of support would i have by having started with a standard Ubuntu (Xenial Xerus 16.04) and added the packages that come in Xubuntu from the same repository?  could that be the cause of not getting any package upgrades?  i do still have Unity installed and can switch to it.

---

### Post by deadflowr on 2019-03-07
You can look at what the status is for all packages with
```
ubuntu-support-status --show-all
```

Note that unsupported might not exactly mean unsupported by rather it also means unknown state of support.
So some listed as unsupported might just be supported but the status was left undefined.

Support means developers will try to fix issues.
No longer supported means developers will no longer try to fix issues.

You'll be able to install any package from the repos until the repos are removed after xenial hits end of life.
But if the packages that are no longer supported are broken the developers won't do anything about it.
Any of that make sense?

Also, Ubuntu now has apt running from a systemd setting,
So updates might be getting installed before you ever run the update script.
More on that here: [https://askubuntu.com/questions/878246/update-doesnt-run-automatically-on-ubuntu-16-10]("https://askubuntu.com/questions/878246/update-doesnt-run-automatically-on-ubuntu-16-10")

You can also check the apt logs at /var/log/apt/history.log

I hope it's not too confusing...

---

### Post by Skaperen on 2019-03-07
file /var/log/apt/history.log is empty.

some of the results from "ubuntu-support-status --show-all" include:

```

Support status summary of 'lt2a':

You have 157 packages (7.2%) supported until April 2019 (Community - 3y)
You have 20 packages (0.9%) supported until April 2021 (Community - 5y)
You have 1083 packages (49.8%) supported until April 2021 (Canonical - 5y)

You have 883 packages (40.6%) that can not/no-longer be downloaded
You have 30 packages (1.4%) that are unsupported
```

that 2nd to last line worries me.  and of the packages still supported there have been no updates since January 18?  my system logs upgrades and removes logs that showed nothing upgraded.  my last log from January 17 shows 37 packages were upgraded.  i have no record of when upgrades were attempted since then.  they are started manually and run in a background (detached) screen session.  i run them about weekly.

is there a way to find out when packages were last upgraded in the repository?

---

### Post by again? on 2019-03-07
You appear to only have the source repo enabled for "xenial-updates main"
> 8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    11    
Missing
```
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
```

Here is a default xenial sources list on github.
[https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1](https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1)

*"While Skaperen fiddled Ubuntu burned"* ;)

---

### Post by Skaperen on 2019-03-07
> **guber2 said:**
> You appear to only have the source repo enabled for "xenial-updates main"

Missing
```
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
```

i put that in line 7.  does the line order matter?  107 packages were upgraded.

> **guber2 said:**
> Here is a default xenial sources list on github.
[https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1](https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1)[URL="https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1"]

should i use this, instead?[/URL]

*> **guber2 said:**
> "While Skaperen fiddled Ubuntu burned" *> **guber2 said:**
> ;)

i don't know why.  the forum keeps adding quote things to split that.  i take them out and it adds them back.

---

### Post by again? on 2019-03-07
> **Skaperen said:**
> i put that in line 7.  does the line order matter?  107 packages were upgraded.

[URL="https://gist.github.com/rohitrawat/60a04e6ebe4a9ec1203eac3a11d4afc1"]

should i use this, instead?[/URL]

It doesn't matter.

You can also restore the default sources by moving your /etc/apt/sources.list file.
Third party repositories aren't affected as they are in the **/etc/apt/sources.list.d** directory.
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
```

Then opening software properties and reselecting sources including the updates tab, which will create a new /etc/apt/sources.list file.
```
software-properties-gtk
```
[ATTACH=CONFIG]282717[/ATTACH] [ATTACH=CONFIG]282718[/ATTACH]

Will give you a basic /etc/apt/sources.list sources file minus the comments and the partner repository (deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner)
(***Note** I'm using bionic to show you this)
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] cat /etc/apt/sources.list**
deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse main universe restricted
deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse main universe restricted
deb http://archive.ubuntu.com/ubuntu bionic-backports multiverse main universe restricted
```

Reload from the GUI or
```
sudo apt update
```

---


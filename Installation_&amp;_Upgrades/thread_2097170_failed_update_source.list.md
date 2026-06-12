---
title: "failed update source.list"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by nutricola on 2012-12-22
Hi 
I am having some trouble with repositories, which I think it is effecting some installation.
I am on Ubuntu quantal

I did apt-get upgrade followed by apt-get update and I got the following errors/warnings:
```
Fetched 21.9 kB in 3s (6,490 B/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://archive.canonical.com/dists/quantal/Release  Unable to find expected entry 'partner/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.switch.ch/ftp/mirror/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.switch.ch/ftp/mirror/ubuntu/dists/quantal-updates/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.switch.ch/ftp/mirror/ubuntu/dists/quantal-backports/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.switch.ch/ftp/mirror/ubuntu/dists/quantal-security/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```my source.list file looks like this
```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal multiverse
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-backports main restricted universe multiverse

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security main restricted
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
deb http://archive.canonical.com/ quantal partner
deb-src http://archive.canonical.com/ quantal partner
```I found several previous post about commenting 'indipendent' and other repository but none of the previous solutions I found worked for me.
Thank you for your help in advance

---

### Post by awam66 on 2012-12-22
Just tried an update/upgrade. Get the same problem. Synaptic wont load either with the following errors
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Not using locking for read only lock file /var/lib/dpkg/lock

Any ideas?

---

### Post by Temporarily on 2012-12-22
Hi 

[nutricola]("http://ubuntuforums.org/member.php?u=1768503")  try to change the mirror please. Can you open the update manager ? If yes , goto "settings" and then at first tab , change the **"Download From" **to the **"main"** server. 

[awam66]("http://ubuntuforums.org/member.php?u=486458") 
I think this is not exactly the same problem as @nutricola has.. 

Please open a terminal (CTRL+ALT+T) and apply the commands below 
```
sudo rm /var/lib/apt/lists/* -vf
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get autoclean & sudo apt-get clean all
sudo apt-get update
```and see if problem solved.

Thank you

---

### Post by nutricola on 2012-12-22
Unfortunately it is not opening. It starts scanning something and then it is giving me the same error I posted from apt-get.
I changed anyway the settings from Ubuntusoftwarecenter, and this gave no improvements.
The only different thing I see is that if I run apt-get update from terminal now  befoe the error there are some numbers coming from some 'hits' , I guess it is finding some updates from the main server which were not detected before

---

### Post by awam66 on 2012-12-22
> **Temporarily said:**
> Hi 

[nutricola]("http://ubuntuforums.org/member.php?u=1768503")  try to change the mirror please. Can you open the update manager ? If yes , goto "settings" and then at first tab , change the **"Download From" **to the **"main"** server. 

[awam66]("http://ubuntuforums.org/member.php?u=486458") 
I think this is not exactly the same problem as @nutricola has.. 

Please open a terminal (CTRL+ALT+T) and apply the commands below 
```
sudo rm /var/lib/apt/lists/* -vf
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get autoclean & sudo apt-get clean all
sudo apt-get update
```and see if problem solved.

Thank you

Thanks for the above,
I booted to recovery mode and did Fix Broken Pakages. This came up with an fsck error asked to [ress F to fix it. Pressed F and all is now well!

---

### Post by Temporarily on 2012-12-22
Glad you solved it [awam66]("http://ubuntuforums.org/member.php?u=486458")


[nutricola]("http://ubuntuforums.org/member.php?u=1768503") please try the commands below 

```
sudo cp /etc/apt/sources.list ~/sources.list.old 
sudo wget "http://pastebin.com/raw.php?i=arCPb5ui" -O /etc/apt/sources.list
sudo apt-get update
``` 

and tell me if now works. 

Thanks

---

### Post by nutricola on 2012-12-22
the same error but this time from US
```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/quantal/Release  Unable to find expected entry 'partner/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```


I don't know if it s related but some time ago, I got some strange warning about -fix-architecture, I am not able to reproduce that error now

---

### Post by nutricola on 2012-12-22
HI
now I also have done
```
 sudo rm /var/lib/apt/lists/* -vf 
sudo rm -rf /etc/apt/sources.list.d

```

and I only have this in the source.list 

```

deb http://archive.ubuntu.com/ubuntu quantal main

```

I seriously don4t understand what4s wrong

---

### Post by grahammechanical on 2012-12-23
@nutricola

The command rm = remove. This is the same as 'delete.' You have just deleted all the scripts in the lists folder. These scripts are a record of the packages on your system and the date they were installed. By comparing what we have on our systems with what is available in the repositories/software sources Update Manager knows what needs updating.

You now need to re-create those scripts. run this command:

```
sudo apt-get update
```

That will rebuild the scripts in the lists folder. What did you do wrong? I do not know but this might be a typing error or it may give us a clue.

> I did apt-get upgrade followed by apt-get update and I got the following errors/warnings:

It is usual to 'update' before 'upgrade.' Update compares the scripts in the lists folder with what is in the repositories. Upgrade downloads and installs any packages that have been updated in the repositories. OK. I agree. It is confusing. That is why in Quantal 12.10 it is made easy by going to the Details page in System Settings or About This Computer.

regards.

---

### Post by nutricola on 2012-12-23
Thank you for your reply.
I have probably been unclear. 
I know what rm is doing. I was hoping to clear up some mess.
I did both combinations  of the command (before and after deleting the files):
first 'sudo apt-get update' and then 'sudo apt-get upgrade' (and the other way around).
And I am still getting the same message even if I have just one line uncommented in the file source.list.

I confirm that right now even if I have only one repository activated (either from the US server, from the Swiss server or from "Main"):
e.g.
```
deb http://archive.ubuntu.com/ubuntu quantal main 
```
I got the message
```

Ign http://archive.ubuntu.com quantal InRelease
Hit http://archive.ubuntu.com quantal Release.gpg
Hit http://archive.ubuntu.com quantal Release
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/Release  Unable to find expected entry 'main/binary-386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by nutricola on 2012-12-24
This is another error I get using dpkg, I don't know if they are related
```

Unknown configuration key `foreign-architecture' found in your `dpkg'
configuration files.  This warning will become a hard error at a later
date, so please remove the offending configuration options and replace
them with `dpkg --add-architecture' invocations at the command line.

```

if I write `dpkg --add-architecture' nothing happens and I get the same error

---

### Post by nutricola on 2012-12-24
this is solved there was something wrong inside /etc/dpkg/dpkg.cfg.d/multiarch

---

### Post by nutricola on 2013-01-10
I am still struggling, I refuse to reinstall the distribution just for this.

I found this three servers in resolv.conf

nameserver 62.2.17.60
nameserver 62.2.24.162
nameserver 62.2.17.61

is it normal ?

---


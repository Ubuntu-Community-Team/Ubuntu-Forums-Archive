---
title: "Upgrading 14.04 developers branch to LTS gives UnboundLocalError: local variable 'e'"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by caliberg on 2014-06-04
I initially used "sudo do-release-upgrade" but was returned with "no new release found".  So then I added the -d flag and that started the upgrade process.  But after a few minutes it errored out with:

File 
"/tmp/ubuntu-release-upgrader-thje6kwo/DistUpgrade/DistUpgradeController.py", 
line 927, in doUpdate 
"connection and retry."), "%s" % e) 


UnboundLocalError: local variable 'e' referenced before assignment 

I couldn't find anybody else who had this problem so I don't really know what to do to successfully finish this upgrade.

---

### Post by grahammechanical on 2014-06-04
It is not clear what version of Ubuntu you started out with. If you started out with Ubuntu Trusty Tahr development branch then just updating as usual would have turned trusty tahr into 14.04 LTS. That is what happened on my installs of trusty tahr.

We cannot upgrade to a new release from the 14.04 development branch as the next new release would be 14.10 and that is not available. The -d flag upgrades from a stable release to the development branch of the next release. So, running do-release-upgrade -d from 14.04 LTS would have upgraded to Utopic Unicorn development branch. You could try

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then run

```
lsb_release -a
```

to see what you have.

For those who do not know, the command apt-get dist-upgrade only upgrades the existing distribution/release. It pulls in any held back updates. It does not upgrade to the next release.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by caliberg on 2014-06-04
You're assumption is correct, I currently have Trusty Tahr development branch, but I'm not having as good of luck as you in turning it into 14.04 LTS.  Whether I run do-release-upgrade or apt-get update or apt-get dist-upgrade, lsb_release -a continues to show the development branch:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty

I do get a lot of forbidden errors though when running sudo apt-get update:

...
W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages)  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by deadflowr on 2014-06-04
> I do get a lot of forbidden errors though when running sudo apt-get update:

...
W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu....-i386/Packages]("http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages")  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead. 				

There's your problem.
Could you post the whole output for 
```
sudo apt-get update
```
and the output for this
```
cat /etc/apt/sources.list
```

I notice the repo line you posted has .ec2 in it. Is this running on Amazon EC2, perhaps?

---

### Post by caliberg on 2014-06-04
Yes, you're correct, and it's a micro instance too so if the upgrade takes a lot of resources that also could be a problem.  So far that hasn't been a problem with Ubuntu.  So the full update output is:

```
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic InRelease
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates InRelease
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic Release.gpg
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates Release.gpg
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic Release
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Sources
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/main Sources
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/universe Sources
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/main amd64 Packages
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/universe amd64 Packages
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/main i386 Packages
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/universe i386 Packages
  403  Forbidden
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/main Translation-en_US
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/main Translation-en
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/universe Translation-en_US
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic/universe Translation-en
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/main Sources
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/universe Sources
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/main amd64 Packages
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/universe amd64 Packages
  403  Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Sources
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/main i386 Packages
  403  Forbidden
Err [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/universe i386 Packages
  403  Forbidden
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/main Translation-en_US
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/main Translation-en
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/universe Translation-en_US
Ign [http://us-west-2.ec2.archive.ubuntu.com](http://us-west-2.ec2.archive.ubuntu.com) utopic-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en_US
W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-amd64/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-amd64/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages)  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead.

```
And here's [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list:
[/FONT][/COLOR]```
## Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
#


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic main
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic main


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic-updates main
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic-updates main


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic universe
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic universe
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic-updates universe
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) utopic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) utopic-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
```

---

### Post by deadflowr on 2014-06-04
I'm not sure that mirror for utopic exists yet?

You can try resetting the repo to trusty.
First make a quick backup copy, just in case
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
```
then change the sources.list to trusty with this quick one liner
```
sudo sed -i -e 's/utopic/trusty/g' /etc/apt/sources.list
```
You can run cat /etc/apt/sources.list again to make sure the lines all changed to trusty.
Then try
```
sudo apt-get update
```
Post errors if you get any.
If no errors, then try
```
sudo apt-get upgrade
```
and maybe 
```
sudo apt-get dist-upgrade
```

Don't know if any of this will help, but you should at least be back with the trusty repos.

---

### Post by caliberg on 2014-06-04
Big help - now get "14.04 LTS" which is perfect&#8230;thanks for the clear and timely information!

---

### Post by deadflowr on 2014-06-04
> **caliberg said:**
> Big help - now get "14.04 LTS" which is perfect…thanks for the clear and timely information!

I'm guessing no errors then?
If so, and you are satisfied with the results
[Please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

If problems with the updating are still happening, post them.

---


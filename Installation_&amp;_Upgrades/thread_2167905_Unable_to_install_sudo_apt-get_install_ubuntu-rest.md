---
title: "Unable to install sudo apt-get install ubuntu-restricted-extras in Karmic (Ubuntu 9.1"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by ndnd on 2013-08-15
Hello all,
I am fairly new to ubuntu. I need to install the codecs for running AVI on Ubuntu 9.10 (Server edition) . So I came to know you can do that by 

```
sudo apt-get install ubuntu-restricted-extras
If you have the latest release which I don't at this time and would like to avoid the upgrade at this point
```

In that case how can I upgrade can someone help me with the exact commands for doing this as I am new and don't want to screw it up.  I tried also to modify the sources.list file found in /etc/apt/ folder I am pasting the contents below 


Sources.list file
```
# 
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

###ndp##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
###ndp##deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

deb [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) karmic main restricted 
deb-src [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) karmic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) karmic-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)  karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

```


I also tried to execute the following commands

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update



sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

This is from medibuntu 
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

But gave the following error

```
Connecting to [www.medibuntu.org|88.191.127.22|:80]("http://www.medibuntu.org|88.191.127.22|:80")... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-08-15 14:37:42 ERROR 404: Not Found.

```

Thanks in advance for your help. 

Regards,
Nipun

---

### Post by QIII on 2013-08-15
Hello!

Karmic is well beyond its End Of Life and is no longer supported -- even the server version stopped receiving support in 2012.  The repos have been moved and are no longer where your sources list think they are.  Thus, you are getting the 404 errors.

Rather than trying to help you find those archived repos, I would suggest that you upgrade to a supported version of Ubuntu by doing a fresh install and work from there.

---

### Post by ndnd on 2013-08-15
Hi,
Thanks for the reply. In the interim is there a way to find codecs for AVI files online and install them? That would be a good temporary fix until I can do a clean install? 

Thanks in advance.

---

### Post by deadflowr on 2013-08-15
Gigantic +1 for simply upgrading over trying to use an old release.

That said, I notice that your sources.list is all mixed up, with both old-release entries and both archive and security entries.
The archive and security entries must be changed as well, or commented(#)out.

This command will help change all the entries to the old-release
```
sudo sed -i -e 's/us.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

However, even if you change the sources.list, It still won't fix the problems with the medibuntu repos.

---

### Post by ndnd on 2013-08-15
Thanks for the reply Deadflowr. I executed the command and as QIII pointed out it didn't allow me to access any packages.  However, if there are any packages available online that I can just download using wget and install them it would at least get me going for now.  I just don't know where I can find the codecs and how to install them mannually.

---

### Post by deadflowr on 2013-08-15
> **ndnd said:**
> Thanks for the reply Deadflowr. I executed the command and as QIII pointed out it didn't allow me to access any packages.  However, if there are any packages available online that I can just download using wget and install them it would at least get me going for now.  I just don't know where I can find the codecs and how to install them mannually.

If you look here
[http://packages.medibuntu.org/precise/index.html](http://packages.medibuntu.org/precise/index.html)

These are the medibuntu packages for precise.
If you click on one of the packages, it'll move you to a download page.
On the left is where the easy to install deb files are(list i386 and amd64)
And on the rightside is where you can find the source packages.

Not sure how helpful it is, but...

---


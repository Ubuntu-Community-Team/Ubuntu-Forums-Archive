---
title: "Installing Kubuntu"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Starcom826 on 2005-06-22
I just installed Ubuntu yesterday, and tried installing KDE today.  I tried apt-get install kubuntu-desktop as root, but it says that I can't install it due to konversation and gives me this error:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: konversation but it is not going to be installed
E: Broken packages


I tried apt-get installing konversation seperately, but it says it requires kdelibs4 version 4:3.4.1, but the repositories only have 4:3.4.1.  I followed the adding repositories guide from ubuntuguide.org, but I'm not sure how to resolve this.  I could install kubuntu-desktop two days ago.  Any help would be appreciated.

---

### Post by SGC on 2005-06-22
Can you post the contents of your **/etc/apt/sources.list** file

---

### Post by Starcom826 on 2005-06-22
My sources file:


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by SGC on 2005-06-22
Add this line to the end of the sources file:
```

deb http://kubuntu.org/hoary-kde341 hoary-updates main

```

Then do **apt-get update** and try to install kubuntu-desktop again.

---

### Post by Starcom826 on 2005-06-22
Thanks.  It's letting me install Kubuntu-desktop now.  Since I read that to be version specific, should I remove it after installing KDE, or leave it there?

---

### Post by SGC on 2005-06-22
[QUOTE=Starcom826]Thanks.  It's letting me install Kubuntu-desktop now.  Since I read that to be version specific, should I remove it after installing KDE, or leave it there?[/QUOTE]
 If you mean the hoary-kde341 repository, I see no harm in leaving it there until a new version of kde is available.

---

### Post by Starcom826 on 2005-06-22
Hehe, well sorry for the trouble but something came up again.  At the end of the installation, k3blibs failed to install.  It had a problem with the md5 checksum.  I tried installing it again with apt-get and I got this:

Preconfiguring packages ...
(Reading database ... 83822 files and directories currently installed.)
Unpacking k3blibs (from .../k3blibs_0.11.23-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/k3blibs_0.11.23-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm hoping its not much of a deal.  I really only wanted to install KDE for the apps like amarok, and not as the user interface.

---

### Post by SGC on 2005-06-22
If it is in the end of the installation , I suppose the kubuntu has been installed except k3b (the cd burrining application) 

So I suggest to restart you computer and try to login to kde. And then do **apt-get install kubuntu-desktop** again which will **resume** the installition and hoppfully fix the k3b problem

---


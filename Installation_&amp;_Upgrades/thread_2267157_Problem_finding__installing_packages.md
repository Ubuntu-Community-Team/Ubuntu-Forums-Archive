---
title: "Problem finding / installing packages"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by ocgltd on 2015-02-27
I'm a long-time Red Hat user struggling to make my way in the Ubuntu world.  I just installed Ubuntu 14 TLS server edition.  I'm trying to add some packages that SHOULD exist but I can't install them!  For example:

apt-get install joe

Should install the joe editor, but I get an error "unable to locate package joe".  I checked my /etc/apt/source.list and I see main, universe, restricted, multiverse.  Why can't this install?

---

### Post by ian-weisser on 2015-02-27
Please show us the *complete* output of
```
sudo apt-get update
sudo apt-get install joe
```

apt and dpkg have lots of helpful-to-the-experienced status messages and error messages that are pure jibberish until you learn them.

---

### Post by bapoumba on 2015-02-27
Could you please post your sources.list :
```
cat /etc/apt/sources.list
```

---

### Post by Bashing-om on 2015-02-27
ocgltd; Hi ! Welcome to 'buntu !

The editor is there :
```

sysop@1404mini:~$ apt-cache show joe
Package: joe
Priority: optional
Section: universe/editors
Installed-Size: 1313
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Josip Rodin <joy-packages@debian.org>
Architecture: amd64
Version: 3.7-2.3ubuntu1
<snip>
Filename: pool/universe/j/joe/joe_3.7-2.3ubuntu1_amd64.deb
<snip>

```

Are you accessing your system as a normal user ( that is the norm ) .. and to execute an administrative task, one must elevate their privileges with the use of 'sudo' , Super User DO. For example:
```

sudo apt-get install joe

```
see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
for a full explanation of 'sudo' .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ocgltd on 2015-02-27
I'm embarrased to say I can even capture the output of these commands.  I have Ubuntu installed in a VM, and I can't get the VMware tools installed so I can't copy and paste text in/out.  I'm caught in a vicious circle....

I'm logged in as root, and the update command shows Hit for main repo, err for other repos (404 errors), and Ign for lst_release/all repos.

Does that help?

---

### Post by bapoumba on 2015-02-27
> **ocgltd said:**
> I'm embarrased to say I can even capture the output of these commands.  I have Ubuntu installed in a VM, and I can't get the VMware tools installed so I can't copy and paste text in/out.  I'm caught in a vicious circle....

I'm logged in as root, and the update command shows Hit for main repo, err for other repos (404 errors), and Ign for lst_release/all repos.

Does that help?

If the universe repos cannot be reached, then yes, you cannot install the package. Now the question is why. If you can reach the main repos, that means you have a functional  internet connection. May be a typo in the sources.list ?

---

### Post by ocgltd on 2015-02-27
Ok - I've got some output now.  Here is /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lst_release -sc) main universe restricted multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lst_release -sc) main universe restricted multiverse
deb cdrom:[Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

and the output of "apt-get update"

```
Ign cdrom://Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty InRelease
Ign cdrom://Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty/main Translation-en_US
Ign cdrom://Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty/main Translation-en
Ign cdrom://Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1) trusty/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/-sc) amd64 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/main amd64 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/universe amd64 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/-sc) i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/-sc) Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/-sc) Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lst_release/universe Translation-en
```

---

### Post by ian-weisser on 2015-02-27
Well, that did tell us a lot.
Your /etc/apt/sources.list is bad.

Here's an example of what it should look more like:
```
deb http://archive.ubuntu.com/ubuntu/ **trusty** main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ **trusty-updates** main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ **trusty-security** main restricted universe multiverse
```

And you can delete (or comment out) the CD-ROM line, unless you happen to leave it in the tray. You have already installed most of those packages.

Once you have fixed sources.list,
do a 'sudo apt-get update' to refresh the package database,
then a 'sudo apt-get upgrade' to pick up bugfixes and security patches,
and then your package manager should work for anything else you wish.

Er, that first 'apt-get upgrade' might be a bit hefty. Allow a bit of time.

---

### Post by ocgltd on 2015-02-27
That did it!

I wonder if I did something wrong during installation...now I wonder what else isn't setup right.  As I'm new to Ubuntu I'm going to treat this as a warning that I messed up somewhere along the installation path and re-install.

Thanks

---

### Post by coldraven on 2015-02-28
I noticed that you are using VMware but if you are just experimenting you could use VirtualBox and get ready-made sever images. I'm lazy and this is a very quick way to get up and running. Install VirtualBox from their site, the version in the Ubuntu Software Centre is usually older.
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by bapoumba on 2015-02-28
Glad to see you got it to work ocgltd :)

---


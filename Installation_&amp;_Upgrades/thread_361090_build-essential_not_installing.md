---
title: "build-essential not installing"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by OmahaVike on 2007-02-13
hello.  i find myself running in circles trying to get build-essential (and other tools) installed through apt.  perhaps a friendly soul will be wandering by my post to help.  would be very much appreciated, since i'm finding myself in a "who's on first" circular reference.

running 6.06
2.6.15-27-386

here's my sources.list
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://dl.ivtvdriver.org/ubuntu dapper all

```

as you can probably tell from the last repository, i'm working on installing ivtv sources to compile.  it's the build-essential that i'm having a problem with.

so i pull an "apt-get install build-essential" and it errors out on dependencies:
```

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed

```

in an effort to understand the problem, i try to "apt-get install libc6-dev" and i find dependency problems:

```

libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is to be installed
E: Broken packages

```

okay, this tells me that either a) my kernel isn't supported for libc6 or b) that i have broken packages.  BUT, i rule out broken packages through syaptic package manager - shows zero broken.

i find that g++ wont be installed either, because of this lineage of dependencies:

g++ depends on g++-4.0 which depends on libstdc++6-4.0-dev which depends on libc6-dev

which brings me back to the problem in my code window above.  yeesh!

any and all guidance is *greatly* appreciated.  i've tried to use my original sources.list, after refreshing and rebooting to find the same problem.  failed dependencies with no broken packages.

thanks in advance!

---

### Post by taurus on 2007-02-14
```
sudo apt-get update
sudo apt-get install build-essential
```

Otherwise, install the Ubuntu CD that you installed Dapper with into the drive and type

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by aysiu on 2007-02-14
Dependency errors usually come from conflicting repositories. I don't know exactly what's conflicting in your sources.list, but please try **[getting a fresh sources.list](http://www.psychocats.net/ubuntu/sources)** and then installing it again: ```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by nalioth on 2007-02-14
Yes, use an official sources.list, Your build-essential is wanting to install 'some other distros' libc6, which will pretty much screw your Ubuntu up.

---

### Post by OmahaVike on 2007-02-15
> **aysiu said:**
> Dependency errors usually come from conflicting repositories. I don't know exactly what's conflicting in your sources.list, but please try **[getting a fresh sources.list](http://www.psychocats.net/ubuntu/sources)** and then installing it again: ```
sudo aptitude update
sudo aptitude install build-essential
```

thank you all for your quick replies.  yes, i did read that the official sources are a problem solver.  in this case, it isn't.  followed the link for the official sources.list, cleaned out the sources.list file and then copied/pasted them from the linked tutorial.  did the CLI update and here's what i see when pulling the trigger on an "aptitude install build-essential"

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
The following NEW packages will be automatically installed:
  g++ g++-4.0 libstdc++6-4.0-dev linux-kernel-headers
The following packages have been kept back:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libpq4 linux-386 linux-image-386
  linux-restricted-modules-386 linux-restricted-modules-common lvm2
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev linux-kernel-headers
0 packages upgraded, 6 newly installed, 0 to remove and 10 not upgraded.
Need to get 7611kB of archives. After unpacking 32.1MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu12 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.0 [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.0-dev [Not Installed]

Score is 35

Accept this solution? [Y/n/q/?]


```

so, i accept (and drumroll as you can tell the outcome)

```

The following packages have been kept back:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libpq4 linux-386 linux-image-386
  linux-restricted-modules-386 linux-restricted-modules-common lvm2
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

wierd stuff, eh.

any other suggestions?  and thanks again for working with me on this.

---

### Post by aysiu on 2007-02-15
Can you try this? ```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential
```

---

### Post by OmahaVike on 2007-02-15
> **aysiu said:**
> Can you try this? ```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential
```

[SIZE="6"]WARNING[/SIZE]

the previous quoted code MAY screw up your grub listing.  if you have a dual boot situation, be prepared to have your 'doze entry possibly wiped out.  mine did.  not crying too much, as i've fought this battle many times before and have a few dozen backups.  please backup your /boot/grub/menu.lst before proceeding.

[SIZE="6"]END WARNING[/SIZE]

anyhow, thank you for the suggestion.  followed your directions.  during the course of events, ubuntu suggested that i reboot after dist-upgrade.  tried to install build-essential before reboot.  same error.  rebooted.  same error.  

```

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

```

egads.  i haven't jacked with the fresh sources.list either.  any other suggestions (other than reinstall the whole OS) would be greatly appreciated.

thanks again for all you do.

---

### Post by confused57 on 2007-02-15
Have you tried to install build-essential via Synaptic Package Manager?  Worth a try, if you haven't.

Your Windows entry in grub should not be affected, if it is located after the line:

### END DEBIAN AUTOMAGIC KERNELS LIST

or before the line:

### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by OmahaVike on 2007-02-16
thank you confused57.  that explains the menu.lst issue.

tried to install through synaptic package manager, and still getting errors:

```

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

```

'twas worth a gamble.

---

### Post by OmahaVike on 2007-02-16
hey gang.  just saw something peculiar.  could this have anything to do with it?

directory listing for /etc/apt:
```

root@mainmachine:/etc/apt# ls -l
total 60
-rw-r--r-- 1 root root   30 Nov 17 18:10 apt.conf
drwxr-xr-x 2 root root 4096 Nov 17 18:14 apt.conf.d
-rw------- 1 root root    0 May 30  2006 secring.gpg
-rw-r--r-- 1 root root 1524 Feb 14 23:08 sources.list
-rw-r--r-- 1 root root 1784 Nov 18 00:34 sources.list.bk1
-rw-r--r-- 1 root root 3576 Feb  5 22:09 sources.list.bk2
-rw-r--r-- 1 root root 1468 Feb 14 23:04 sources.list.bk3
drwxr-xr-x 2 root root 4096 Feb  5 22:02 sources.list.d.bakup
-rw-r--r-- 1 root root 3406 Nov 18 00:39 sources.list.expanded
-rw-r--r-- 1 root root 1422 Feb  9 23:03 sources.list.orig
-rw-r--r-- 1 root root 1784 Feb  5 22:12 sources.list.save
-rw------- 1 root root 1200 May 30  2006 trustdb.gpg
-rw-r--r-- 1 root root 5913 Feb 13 22:30 trusted.gpg
-rw-r--r-- 1 root root 4743 Feb  5 22:58 trusted.gpg~
root@mainmachine:/etc/apt#


```

are those two sub-directories supposed to be in here?

not sure if there is some other overriding source list somewhere else.

---

### Post by OmahaVike on 2007-02-17
alright....  hoping this might help someone see a blaringly simple hole:

apt-get update:
```

Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Fetched 5B in 1s (3B/s)
Reading package lists... Done

```

all looks fairly swell, eh?  okay, on to build-essential immediately thereafter:

```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

```

to my novice eyes, this all appears good.  anyone?

---

### Post by samkline on 2007-02-19
having the same exact problem.

anyone found a solution?

---

### Post by samkline on 2007-02-19
ok, i found a solution. (at least, it works for me)

1) open synaptic
2) find libc6
3) on the menu, go to package -> force version
4) choose 2.4-1ubuntu12.3
5) apply changes (meaning, downgrade/install) and close synaptic
6) sudo apt-get install build-essential

good luck,

---

### Post by OmahaVike on 2007-02-19
thanks for trying samkline.

not presented with a 2.4-1ubuntu12.3 version for libc6 (that or dev).  only 2.4-1ubuntu12, which is currently installed.  boy, me thinks something is really jacked up in my apt settings.

---

### Post by voam on 2007-03-10
samkline's method has worked for me even though the options for the versions were different then the ones on his system. Basically I had two options and chose the lesser version number than was currently installed. 

Now I can give banshee a shot with podcasts.

Thanks!

---


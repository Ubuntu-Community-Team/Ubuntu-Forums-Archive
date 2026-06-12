---
title: "Update Manager/Software Center/apt-get problem &quot;The package system is broken&quot;"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by kakar on 2014-04-21
I was recently updating my ubuntu 12.04 LTS after a long time, however, in the midst of the approx 500 files that were downloading in the process, my laptop froze up and would not respond. So I did what any one would and chose to hard kill it. Thereafter once my system turned back on, I could not run the update manager and it gives the following error:-
[CENTER][ATTACH=CONFIG]252322[/ATTACH][/CENTER]

If I run the software center, i get the following error, before it even starts up completely:- 
[CENTER][ATTACH=CONFIG]252323[/ATTACH][/CENTER]

On running repair thereunder, I get a dialogue box that says an error was encountered in installation removal of a package. This is the output for the details:-

```
installArchives() failed: perl: warning: Setting locale failed.perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 libhcrypto4-heimdal:i386
 libhcrypto4-heimdal
Error in function: 
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)



```

I also tried to run ```
apt-get -f install
```

it started out ok, however, i get the following output and the command ends in error:-

```
The following extra packages will be installed:  libhcrypto4-heimdal:i386
The following packages will be upgraded:
  libhcrypto4-heimdal:i386
1 upgraded, 0 newly installed, 0 to remove and 458 not upgraded.
2 not fully installed or removed.
Need to get 0 B/104 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
Errors were encountered while processing:
 libhcrypto4-heimdal:i386
 libhcrypto4-heimdal
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


As of now I cant install/update/uninstall anything either from the software center, update center or from the command line. 

I need some help!!! 

Help!!!

---

### Post by kc1di on 2014-04-21
Try this in a terminal ```
sudo dpkg --configure -a
```

---

### Post by kakar on 2014-04-22
hey thanks for the input, however, no success..
```
random@crackeur:~$ sudo dpkg --configure -a[sudo] password for random: 
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
Errors were encountered while processing:
 libhcrypto4-heimdal
 libhcrypto4-heimdal:i386
random@crackeur:~$ 



```

---

### Post by kakar on 2014-04-22
Ok.. from whats going on, I can gather theres some problem with processing these:-

 libhcrypto4-heimdal
 libhcrypto4-heimdal:i386

What does "is in a different version" imply?

---

### Post by kakar on 2014-04-22
I am ashamed to do so, but BUMP     [-o<

---

### Post by kakar on 2014-04-24
The problem was broken dependencies, and because synaptic wasnt there on my system, i had to terminal it... this really helped: [https://mergy.org/2013/03/repairing-a-badly-damaged-package-system-in-ubuntu/](https://mergy.org/2013/03/repairing-a-badly-damaged-package-system-in-ubuntu/)

```
[COLOR=#004ED0 !important][FONT=inherit]sudo [/FONT][/COLOR][COLOR=#000000][FONT=inherit]apt[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]-[/FONT][/COLOR][COLOR=#004ED0 !important][FONT=inherit]get [/FONT][/COLOR][COLOR=#000000][FONT=inherit]build[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]dep[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit] [/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]<[/FONT][/COLOR][COLOR=#800080 !important][FONT=inherit]package[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]>[/FONT][/COLOR]
```

followed by 

```
[COLOR=#004ED0 !important][FONT=inherit]sudo [/FONT][/COLOR][COLOR=#000000][FONT=inherit]apt[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]-[/FONT][/COLOR][COLOR=#004ED0 !important][FONT=inherit]get [/FONT][/COLOR][FONT=inherit][COLOR=#000000]install[/COLOR][/FONT][COLOR=#006FE0 !important][FONT=inherit] [/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]<[/FONT][/COLOR][COLOR=#800080 !important][FONT=inherit]package[/FONT][/COLOR][COLOR=#006FE0 !important][FONT=inherit]>[/FONT][/COLOR]
```

---

### Post by kakar on 2014-04-27
still not fixed.. dpkg throws up an error processing libhcrypto4-heimdal and libhcrypto4-heimdal:i386

it says:- 

```
kakar@crackeur:~$ sudo dpkg --configure libhcrypto4-heimdal libhcrypto4-heimdal:i386dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
Errors were encountered while processing:
 libhcrypto4-heimdal
 libhcrypto4-heimdal:i386
kakar@crackeur:~$ sudo dpkg --configure libhcrypto4-heimdal libhcrypto4-heimdal:amd64 libhcrypto4-heimdal:i386
Package libhcrypto4-heimdal listed more than once, only processing once.
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
Errors were encountered while processing:
 libhcrypto4-heimdal
 libhcrypto4-heimdal:i386


kakar@crackeur:~$ sudo dpkg --configure libhcrypto4-heimdal --force-configure-any dpkg: error: package name in specifier '--force-configure-any' is illegal: must start with an alphanumeric character
kakar@crackeur:~$ sudo dpkg --configure libhcrypto4-heimdal --force-configure-any libhcrypto4-heimdal
dpkg: error: package name in specifier '--force-configure-any' is illegal: must start with an alphanumeric character
kakar@crackeur:~$ sudo dpkg --configure --force-configure-any libhcrypto4-heimdal
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
Errors were encountered while processing:
 libhcrypto4-heimdal
kakar@crackeur:~$ sudo dpkg --configure --force-configure-any libhcrypto4-heimdal:i386
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
Errors were encountered while processing:
 libhcrypto4-heimdal:i386
kakar@crackeur:~$ sudo dpkg --configure --force-configure-any libhcrypto4-heimdal:amd64
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
Errors were encountered while processing:
 libhcrypto4-heimdal
kakar@crackeur:~$ sudo dpkg --configure --force-configure-any libhcrypto4-heimdal
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
Errors were encountered while processing:
 libhcrypto4-heimdal
kakar@crackeur:~$ sudo dpkg --configure --force-configure-any libhcrypto4-heimdal:i386 libhcrypto4-heimdal
dpkg: error processing libhcrypto4-heimdal:i386 (--configure):
 libhcrypto4-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhcrypto4-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
dpkg: error processing libhcrypto4-heimdal (--configure):
 libhcrypto4-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhcrypto4-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
Errors were encountered while processing:
 libhcrypto4-heimdal:i386
 libhcrypto4-heimdal



```

its narrowed down to interdependant dependencies... so... anyone know how to fix this?

---

### Post by kakar on 2014-04-27
i think, and this is a novice guess, that getting these packages from other sources and installing them might help solve the problem? becuase as far as I can figure out, the problem has to do with different versions of these packages, so logically deducing, getting the latest versions of the packages and installing them manually should fix the problem?

can anyone guide me in this venture? please?

[ATTACH=CONFIG]252556[/ATTACH]
[http://packages.ubuntu.com/precise/libhcrypto4-heimdal](http://packages.ubuntu.com/precise/libhcrypto4-heimdal)

---

### Post by kakar on 2014-04-27
Also, if my update manager, if I press "install updates", throws up this error
```
The following packages have unmet dependencies:

libhcrypto4-heimdal: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is installed
libhcrypto4-heimdal:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.5 is installed



```

does this mean that the package mentioned former depends ON the package mentioned later, or does it mean that the package mentioned later depends on the package mentioned former?

---

### Post by bapoumba on 2014-04-27
Please post your sources.list and the ppa you may be using :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

Version conflicts often come from the repos you are using.

---

### Post by iampokpak on 2014-04-27
I have the same problem.

Here's my source.list
root@PopularPokapak:~# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise main restricted
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates main restricted
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise universe
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise universe
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates universe
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise multiverse
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise multiverse
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates multiverse
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-backports main restricted universe multiverse


deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security main restricted
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security main restricted
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security universe
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security universe
deb [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security multiverse
deb-src [http://mirrors.psu.ac.th/pub/ubuntu/](http://mirrors.psu.ac.th/pub/ubuntu/) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
root@PopularPokapak:~# ls /etc/apt/sources.list.d
danielrichter2007-grub-customizer-precise.list  mendeleydesktop.list.save
dropbox.list                                    private-ppa.launchpad.net_commercial-ppa-uploaders_pdfstudio7demo_ubuntu.list
dropbox.list.save                               private-ppa.launchpad.net_commercial-ppa-uploaders_pdfstudio7demo_ubuntu.list.save
google-chrome.list.save                         tualatrix-ppa-precise.list
google-talkplugin.list                          tualatrix-ppa-precise.list.save
google-talkplugin.list.save                     ubuntu-wine-ppa-precise.list
mendeleydesktop.list                            ubuntu-wine-ppa-precise.list.save

Thank you,
pp

---

### Post by bapoumba on 2014-04-27
@iampokpak, do you have the same problem with the same libraries ? More precisely, these ones :
libhcrypto4-heimdal
libhcrypto4-heimdal:i386

---

### Post by kakar on 2014-04-28
cat /etc/apt/sources.list

```
 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ precise universe
deb-src http://archive.ubuntu.com/ubuntu/ precise universe
deb http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main



```

ls /etc/apt/sources.list.d

```


precise-dell.list  ubuntu-extras.list

 
```

---

### Post by bapoumba on 2014-04-28
I've browsed through the Dell repository and I guess I have a hard time to find where the libs are coming from.

So please run :
```
apt-cache policy libhcrypto4-heimdal
apt-cache policy libhcrypto4-heimdal:i386
```

---

### Post by kakar on 2014-04-28
```
libhcrypto4-heimdal:  Installed: 1.6~git20120311.dfsg.1-2ubuntu0.1
  Candidate: 1.6~git20120311.dfsg.1-2ubuntu0.1
  Version table:
 *** 1.6~git20120311.dfsg.1-2ubuntu0.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.6~git20120311.dfsg.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages



```
```
libhcrypto4-heimdal:i386:  Installed: 1.6~git20120311.dfsg.1-2
  Candidate: 1.6~git20120311.dfsg.1-2ubuntu0.1
  Version table:
     1.6~git20120311.dfsg.1-2ubuntu0.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
 *** 1.6~git20120311.dfsg.1-2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status



```

Thanks man... also, why do I need the amd64 packages anyway? mine is an intel core i5..

---

### Post by bapoumba on 2014-04-28
Please try do disable the dell repos and see if it helps. The installed versions are the ones from the main repos, so the conflict version comes from some other place.

---

### Post by kakar on 2014-05-04
Hey,
first off thanks for taking out time.. I tried that too.. no change in status. Advice further? Also, should I attempt to get the latest versions of those files and install them manually? could that help?

---

### Post by bapoumba on 2014-05-04
OK, would you know where these libs were coming from ?
I'm guessing you ran the update/upgrade after removing the Dell repos.

Please try this and see if you can find which package you installed that brought them in :
```
apt-cache rdepends libhcrypto4-heimdal
apt-cache rdepends libhcrypto4-heimdal:i386
```

As an example of what you should get, leafpad being the simple text editor for lubuntu :
```
apt-cache rdepends leafpad
leafpad
Reverse Depends:
  lxde
  lubuntu-desktop
```

---

### Post by kakar on 2014-06-23
Hey bapoumba,

Ive been away to the himalayas travelling and trekking for the past month or so. Its been so much fun and the mountains are just so beautiful, but now its back to work! :)

Ok.. the I had purchased this particular laptop from Dell, a vostro and it came preloaded with Ubuntu 12.04. So I believe that when Dell loaded ubuntu 12.04, they put certain packages to customise/enhance the ubuntu install, and that is where these packages probably come from. 

The output for "apt-cache rdepends libhcrypto4-heimdal" is:-
```
 libhcrypto4-heimdal
Reverse Depends:
  libhcrypto4-heimdal:i386
  libhcrypto4-heimdal:i386
  libotp0-heimdal
  heimdal-servers
  heimdal-kdc
  heimdal-kcm
  heimdal-clients
  libkrb5-26-heimdal
  libkdc2-heimdal
  libhx509-5-heimdal
  libheimntlm0-heimdal
  libgssapi3-heimdal
  heimdal-multidev
  libhcrypto4-heimdal:i386
  libhcrypto4-heimdal:i386
  samba4-testsuite
  libotp0-heimdal
  libdcerpc-server0
  heimdal-servers
  heimdal-kdc
  heimdal-kcm
  heimdal-clients
  libkrb5-26-heimdal
  libkdc2-heimdal
  libhx509-5-heimdal
  libheimntlm0-heimdal
  libgssapi3-heimdal
  heimdal-multidev

```


and for "apt-cache rdepends libhcrypto4-heimdal:i386"
```
 libhcrypto4-heimdal:i386
Reverse Depends:
  libotp0-heimdal:i386
  heimdal-servers:i386
  heimdal-kdc:i386
  heimdal-kcm:i386
  heimdal-clients:i386
  libkrb5-26-heimdal:i386
  libkdc2-heimdal:i386
  libhx509-5-heimdal:i386
  libheimntlm0-heimdal:i386
  libgssapi3-heimdal:i386
  heimdal-multidev:i386
  libhcrypto4-heimdal
  libhcrypto4-heimdal
  samba4-testsuite:i386
  libotp0-heimdal:i386
  libdcerpc-server0:i386
  heimdal-servers:i386
  heimdal-kdc:i386
  heimdal-kcm:i386
  heimdal-clients:i386
  libkrb5-26-heimdal:i386
  libkdc2-heimdal:i386
  libhx509-5-heimdal:i386
  libheimntlm0-heimdal:i386
  libhcrypto4-heimdal
  libhcrypto4-heimdal
  libgssapi3-heimdal:i386
  heimdal-multidev:i386

```

I wonder if that is of any help. However, I wonder if there is any other way to repair the package catalog.. Also, I tried to install synaptic manually via deb, because I have a nagging feeling that installing synaptic should help me somehow to uninstall the troublesome packages with much more ease. However, a warning popped up saying that I would not get updates for various ubuntu packages in the future if I install synaptic. I dont know what to think anymore.. :confused:

---

### Post by bapoumba on 2014-06-23
Have you disabled the dell third party repo ?

Hey, looks like a nice trip :jealous:

---

### Post by kakar on 2014-06-23
Yep I did. It was. Havent seen so many stars in the night sky for a while..

---

### Post by bapoumba on 2014-06-23
Hmm, just to make sure, did you run **sudo apt-get update** before running **sudo apt-get upgrade** ?

(watching stars in clear skies and no light pollution is like dreaming all awake).

---


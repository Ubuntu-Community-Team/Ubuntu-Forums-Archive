---
title: "Error: The package update-manager needs to be reinstalled"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by petros.han on 2010-12-22
Hi All,

My Ubuntu is 10.04 64bit. 

```

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```I have an error message when I try to install a software with apt-get. 

```

$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.

```And when I open the Update Manager  (System->Administration->UpdateManager), it said "Not all updates  can be installed", thus I hit the "Partial Upgrade" button. But it  returned me "Cannot upgrade. Your python install is corrupted. Please  fix the 'usr/bin/python' symlink."

So, I've attempted to fix the error with the explanation in the link "[PackageManagerTroubleshootingProcedure]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure?action=fullsearch&context=180&value=linkto%3A%22PackageManagerTroubleshootingProcedure%22")" ([https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)). However it was failed. I have had the same error message when I run

```

LANG=C;sudo apt-get -f install 
```in the step4 in the link. What can I do?? :confused:
Please let me know~~ Many thanks in advance.

Petros

---

### Post by susema on 2010-12-22
Try this;

```
sudo apt-get remove --purge update-manager && sudo apt-get install update-manager
```

---

### Post by sikander3786 on 2010-12-22
From Applications > Accessories > Terminal, post the output of these commands.

```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags instead of [quote] tags.

---

### Post by dino99 on 2010-12-22
sudo rm /var/cache/apt/archives/*

then update/upgrade

better to use synaptic to fix dependencies

---

### Post by petros.han on 2010-12-23
@[susema]("http://ubuntuforums.org/member.php?u=1184724"), the command returned the same error message...

@[sikander3786]("http://ubuntuforums.org/member.php?u=806649"), Thanks! I tried and the outputs are as below.

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.

$ sudo apt-get update && sudo apt-get upgrade
Hit http://security.ubuntu.com dapper-security Release.gpg
Hit http://archive.ubuntu.com lucid Release.gpg
Hit http://archive.ubuntu.com dapper Release.gpg
Hit http://archive.ubuntu.com dapper-updates Release.gpg
Hit http://archive.ubuntu.com dapper-backports Release.gpg
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com lucid Release
Hit http://archive.ubuntu.com dapper Release   
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://security.ubuntu.com dapper-security/restricted Sources    
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.

```@[dino99]("http://ubuntuforums.org/member.php?u=129712"), Thanks, but there is a directory named partial...
```
$ sudo rm /var/cache/apt/archives/*   
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
```

---

### Post by dino99 on 2010-12-23
hey dude, are you awake ?

whats that sources mess: dapper+lucid ?

you need to choose but dapper is outdated nowadays :(

sudo apt-get plug brain

---

### Post by sikander3786 on 2010-12-23
As mentioned by *dino99*, there is a problem with your sources.list. This is what you need to do.

Backup your existing sources.list:

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bad
```

Generate a new one:

```
gksudo gedit /etc/apt/sources.list
```

And copy/paste all this text in that one.

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb http://uk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
```

Save and close. Once again run these commands step-by-step.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get upgrade
```

Keep on posting the outputs ;-)

The above sources.list I posted was intended for UK. If that doesn't work for you, generate a new one here.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

After selecting your Ubuntu release and Country, you need everything from "Ubuntu Branches", Security and Updates from "Ubuntu Updates" and everything from "Ubuntu Partner Repos".

---

### Post by petros.han on 2010-12-23
dino99, sikander3786,

Thanks a lot. :D I made a new sources.list and it seems ok. However it returned an error when I run 
```
$ sudo apt-get install -f

```

The output is really long, so I got only last part of it. 

```
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-libvirt 0.7.5-5ubuntu27.3 (using .../python-libvirt_0.7.5-5ubuntu27.8_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.134.11_all.deb
 /var/cache/apt/archives/update-manager-core_1%3a0.134.11_amd64.deb
 /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/gwibber_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/gwibber-service_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb
 /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
namshik@namshik-desktop:~$ 
namshik@namshik-desktop:~$ 
namshik@namshik-desktop:~$ 
namshik@namshik-desktop:~$ 
namshik@namshik-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  gwibber gwibber-service libvirt-bin python-libvirt update-manager update-manager-core
Suggested packages:
  gwibber-themes
The following packages will be upgraded:
  gwibber gwibber-service libvirt-bin python-libvirt update-manager update-manager-core
6 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
14 not fully installed or removed.
Need to get 0B/2,096kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163170 files and directories currently installed.)
Preparing to replace update-manager 1:0.134.10 (using .../update-manager_1%3a0.134.11_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.134.11_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace update-manager-core 1:0.134.10 (using .../update-manager-core_1%3a0.134.11_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.134.11_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch 0.6.4-0ubuntu3 (using .../python-desktopcouch_0.6.4-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch-records 0.6.4-0ubuntu3 (using .../python-desktopcouch-records_0.6.4-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace gwibber 2.30.2-0ubuntu3 (using .../gwibber_2.30.3-0ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/gwibber_2.30.3-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace gwibber-service 2.30.2-0ubuntu3 (using .../gwibber-service_2.30.3-0ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/gwibber-service_2.30.3-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace libvirt-bin 0.7.5-5ubuntu27.7 (using .../libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    start: Job is already running: libvirt-bin
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-libvirt 0.7.5-5ubuntu27.3 (using .../python-libvirt_0.7.5-5ubuntu27.8_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.134.11_all.deb
 /var/cache/apt/archives/update-manager-core_1%3a0.134.11_amd64.deb
 /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/gwibber_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/gwibber-service_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb
 /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thank you.:o

---

### Post by sikander3786 on 2010-12-23
Did you try this command first?

```
sudo apt-get clean
```???

If yes, try this.

```
sudo rm -R /var/cache/apt/archives/*
```

And then,

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by petros.han on 2010-12-23
sikander3786, 

Yes, I did the command, thus I tried it.
```

sudo rm -R /var/cache/apt/archives/*
```
Then did this.
```

sudo apt-get update
```

But... it returned...
```

$ sudo apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.

```
do i need to make the " /var/cache/apt/archives/partial" directory???

Many thanks! :D

---

### Post by dino99 on 2010-12-23
> **petros.han said:**
> dino99, sikander3786,

Thanks a lot. :D I made a new sources.list and it seems ok. However it returned an error when I run 
```
$ sudo apt-get install -f

```

Thank you.:o

i've a doubt: you are not trying a dist-upgrade from Dapper to Lucid indeed ?

for a clean install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sikander3786 on 2010-12-23
You can try creating a partial directory.

But I would also suggest a clean install in the current situation. Let us know what you want to do?

---

### Post by petros.han on 2010-12-23
sikander3786, 

I made the directory, then I could update. However when I tried this.

```
sudo apt-get install -f

```

Ubuntu returned the same error...
```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  gwibber gwibber-service libvirt-bin python-libvirt update-manager update-manager-core
Suggested packages:
  gwibber-themes
The following packages will be upgraded:
  gwibber gwibber-service libvirt-bin python-libvirt update-manager update-manager-core
6 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
14 not fully installed or removed.
Need to get 2,096kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager 1:0.134.11 [803kB]
Get: 2 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.11 [201kB]
Get: 3 http://uk.archive.ubuntu.com/ubuntu/ lucid/main python-desktopcouch 0.6.4-0ubuntu3 [28.7kB]
Get: 4 http://uk.archive.ubuntu.com/ubuntu/ lucid/main python-desktopcouch-records 0.6.4-0ubuntu3 [29.7kB]
Get: 5 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main gwibber 2.30.3-0ubuntu1 [320kB]
Get: 6 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main gwibber-service 2.30.3-0ubuntu1 [60.9kB]
Get: 7 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main libvirt-bin 0.7.5-5ubuntu27.8 [596kB]
Get: 8 http://uk.archive.ubuntu.com/ubuntu/ lucid-updates/main python-libvirt 0.7.5-5ubuntu27.8 [57.4kB]
Fetched 2,096kB in 0s (3,135kB/s)      
(Reading database ... 163170 files and directories currently installed.)
Preparing to replace update-manager 1:0.134.10 (using .../update-manager_1%3a0.134.11_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.134.11_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace update-manager-core 1:0.134.10 (using .../update-manager-core_1%3a0.134.11_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.134.11_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch 0.6.4-0ubuntu3 (using .../python-desktopcouch_0.6.4-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-desktopcouch-records 0.6.4-0ubuntu3 (using .../python-desktopcouch-records_0.6.4-0ubuntu3_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace gwibber 2.30.2-0ubuntu3 (using .../gwibber_2.30.3-0ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/gwibber_2.30.3-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace gwibber-service 2.30.2-0ubuntu3 (using .../gwibber-service_2.30.3-0ubuntu1_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/gwibber-service_2.30.3-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace libvirt-bin 0.7.5-5ubuntu27.7 (using .../libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    start: Job is already running: libvirt-bin
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace python-libvirt 0.7.5-5ubuntu27.3 (using .../python-libvirt_0.7.5-5ubuntu27.8_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.134.11_all.deb
 /var/cache/apt/archives/update-manager-core_1%3a0.134.11_amd64.deb
 /var/cache/apt/archives/python-desktopcouch_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/python-desktopcouch-records_0.6.4-0ubuntu3_all.deb
 /var/cache/apt/archives/gwibber_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/gwibber-service_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/libvirt-bin_0.7.5-5ubuntu27.8_amd64.deb
 /var/cache/apt/archives/python-libvirt_0.7.5-5ubuntu27.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Help me~~~ :confused:

---

### Post by petros.han on 2010-12-23
sikander3786, 

We posted at the same time... :D
I am not sure what is "a clean install", but if it is more perfect way to solve the problems... then YES, i would like to have a go. Please let me know what I can do! Thanks!

:p

---

### Post by sikander3786 on 2010-12-23
As you have been using dapper repos on Lucid, it likely broke more than enough on your sytem and then a re-install of Ubuntu is the best option here.

Things you need:

1. Strong backups of everything important on your HDD.

2. Ubuntu ISO image.

3. CD-R or a USB drive (if your Bios is capable of booting from USB).

4. An hour of free time and some courage :-)

---

### Post by petros.han on 2010-12-23
dino99, sikander3786,

Thanks, so re-install is the best way... huhu.. 
I now want to know what is the reason to prevent this happen again. I think I haven't done anything. One day, the update-manage did not work, and I tried to fix it... that's all. :confused:

---

### Post by sikander3786 on 2010-12-23
> I now want to know what is the reason to prevent this happen again.

By mistake, you added those dapper repos. We can't help you prevent you from that as you are doing it yourself :-)

Only an adivce, follow the guides/links you trust. Or before changing any configuration files, search the forums or ask the forums.

Ubuntuforums is the trusted place and mostly, it has answers to anything you want. Or if not, you can start a new thread any time.

Let us know if you need any help regarding re-install.

Good Luck!

---


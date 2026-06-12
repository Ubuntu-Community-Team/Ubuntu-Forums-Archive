---
title: "Synaptic stuck on bad flex install"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by ckuecker on 2009-12-11
Hi,

I tried to install flex to support a development system I was building. The install failed.

Now, every time I start Synaptic to install another package, I get errors related to that bad flex install. I tried to uninstall flex, but it won't go away.

Is there a directory with the corrupted files in it that i can delete so i can try again?

Chuck Kuecker

---

### Post by earthpigg on 2009-12-11
hi,

can you show us the exact error messages?

try to install something trivial via apt-get at the command line, and show us what it tells you:

```
sudo apt-get install htop
```

---

### Post by ckuecker on 2009-12-11
Here's the results. Not sure what the three packages "not fully installed or removed" include besides flex.

Chuck

ckuecker@ckenterprises:/opt/Freescale$ sudo apt-get install htop
[sudo] password for ckuecker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 55.5kB/299kB of archives.
After this operation, 201kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe htop 0.8.1-4ubuntu1 [55.5kB]
Fetched 55.5kB in 1s (40.7kB/s)
(Reading database ... 115068 files and directories currently installed.)
Preparing to replace flex 2.5.35-6ubuntu1 (using .../flex_2.5.35-6ubuntu1_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/flex_2.5.35-6ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Selecting previously deselected package htop.
Unpacking htop (from .../htop_0.8.1-4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/flex_2.5.35-6ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by earthpigg on 2009-12-11
ive never had that problem, so i won't advocate any one potential solution over another...

...but google searching for "Sub-process /usr/bin/dpkg returned an error code (1)" gave me a promising result.

take a look at [this thread]("http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/").

---

### Post by ckuecker on 2009-12-11
Deleted the files recommended. No joy. Here's what I see:

ckuecker@ckenterprises:/var/cache/apt/archives$ sudo apt-get -f install flexReading package lists... Done
Building dependency tree       
Reading state information... Done
flex is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flex (2.5.35-6ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing flex (--configure):
 subprocess post-installation script returned error exit status 1
Setting up autoconf (2.63-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flex
 autoconf
 automake
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried forcing an install of autoconf:

ckuecker@ckenterprises:/var/cache/apt/archives$ sudo apt-get -f install autoconfReading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flex (2.5.35-6ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing flex (--configure):
 subprocess post-installation script returned error exit status 1
Setting up autoconf (2.63-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flex
 autoconf
 automake
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've got a feeling there's a history file of some sort involved here that's not letting things run correctly.

Chuck

---

### Post by seeker5528 on 2009-12-11
Based on [this](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/330049) you probably have an incompatible version of install-info installed somewhere.

At the command line try typing:

```
which -a install-info
```

On my system I have it showing at two locations '/usr/sbin/' and '/usr/bin/' if one shows up in a different location on your system, that is probably the offending one.

Later, Seeker

---

### Post by ckuecker on 2009-12-12
So far, everything checks out. I've only got those two files:

ckuecker@ckenterprises:/var/cache/apt/archives$ which -a install-info
/usr/local/bin/install-info
/usr/sbin/install-info

Synaptic seems to be working otherwise - it just irritates me to keep getting error messages - it's distracting.

Chuck

---

### Post by ckuecker on 2009-12-12
Spoke too soon - I just tried to install xinetd, and Synaptic failed on the flex error, and never got to the new install. 

Now, it's critical I get this to work. I need xinetd to be able to get tftp working, so I can load stuff into my project.

Chuck

---

### Post by seeker5528 on 2009-12-13
Don't know what's going on there.

On my system if I do:

```
echo $PATH
```

'/usr/sbin' is in the path before '/usr/bin'

In addition to checking the path do:

```
/usr/sbin/install-info --version
/usr/bin/install-info --version
```

to compare the versions. If the versions are different or '/usr/bin is in the path before '/usr/sbin' try to rename the one in '/usr/bin', the one in /usr/sbin should be the one that was part of dpkg.

In Lucid and Debian unstable these appear to both be the same version, but I don't know how long that has been the case.

If '/usr/bin' shows in the path before '/usr/sbin' then you need to figure out where the path is being changed. The default path should be specified in '/etc/environment', it could be set in '/etc/profile' as well. The user specific path would be in '~/.bash_profile', '`/.profile', or it could be set by some script that you run.

Later, Seeker

---

### Post by ckuecker on 2009-12-13
Looked at the PATH. I had changed it to put it in the right order, but forgot that the changes to /etc/environment would not take until I restarted, so did that.

I'm still getting trouble with automake and autoconf. I used apt-get to remove automake, autoconf, and flex - no errors on the remove. So, I tried reinstalling with apt-get.

```

ckuecker@ckenterprises:~$ sudo apt-get -f install automake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
automake is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up autoconf (2.63-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 autoconf
 automake
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I've Googled looking for answers, and found many have had similar troubles. Getting discouraged here.

Chuck

---

### Post by seeker5528 on 2009-12-14
Remove autoconf and automake then type:

```
apt-get check
dpkg -C
```

To see if there is any other problems they report.

The only thing else I can think of to try without resorting to more extreme options is:

```
apt-get install --reinstall dpkg install-info
```

If you have any PPAs or other unoffical repositories enabled you should probably disable these first, and if you get a message that looks like one of these may have been replaced by a newer version that is not from the normal list of Ubuntu repositories try:

```
apt-get install --reinstall --force-yes dpkg install-info
```

I have not actually tried to force a downgrade this way, so if it looks like that is what is needed you might have to go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for and download the versions that go with your version of Ubuntu, then do:

```
dpkg -i --force-downgrade dpkg*.deb install-info*.deb
```

: a more extreme option is to choose the 'safe boot' option at the grub menu and when you get the the safe boot menu choose the dpkg repair option, which will rewrite your sources.list file disabling third party repositories you may have added there or added by creating files in '/etc/apt/sources.list.d/' then try to add/remove things to get you back to a more default list of installed packages. Not necessarily the best option, but if you are down to a point where your alternative is the re-install, it's worth a shot.

Later, Seeker

---

### Post by ckuecker on 2009-12-14
Tried everything. Here's the results:

```

sudo apt-get check
[sudo] password for ckuecker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  automake: Depends: autoconf (>= 2.60) but it is not installed
E: Unmet dependencies. Try using -f.

ckuecker@ckenterprises:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 automake             A tool for generating GNU Standards-compliant Makefiles

ckuecker@ckenterprises:~$ sudo apt-get install --reinstall dpkg install-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of install-info is not possible, it cannot be downloaded.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  automake: Depends: autoconf (>= 2.60) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

ckuecker@ckenterprises:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  autoconf
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc gettext
The following NEW packages will be installed:
  autoconf
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/508kB of archives.
After this operation, 1913kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package autoconf.
(Reading database ... 115155 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.63-2ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up autoconf (2.63-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 autoconf
 automake
E: Sub-process /usr/bin/dpkg returned an error code (1)

ckuecker@ckenterprises:~$ sudo apt-get install --reinstall --force-yes dpkg install-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of install-info is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 2354kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/main dpkg 1.14.24ubuntu1 [2354kB]
Fetched 2354kB in 19s (123kB/s)                                                
(Reading database ... 115227 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu1 (using .../dpkg_1.14.24ubuntu1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.14.24ubuntu1) ...

Setting up autoconf (2.63-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing autoconf (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of automake:
 automake depends on autoconf (>= 2.60); however:
  Package autoconf is not configured yet.
dpkg: error processing automake (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 autoconf
 automake
E: Sub-process /usr/bin/dpkg returned an error code (1)

ckuecker@ckenterprises:~$ sudo dpkg -i --force-downgrade dpkg*.deb install-info*.deb
dpkg: error processing dpkg*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing install-info*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 dpkg*.deb
 install-info*.deb


```

Trying the safe mode reboot next. Will report the results.

Chuck

---

### Post by seeker5528 on 2009-12-14
> **ckuecker said:**
> ckuecker@ckenterprises:~$ sudo dpkg -i --force-downgrade dpkg*.deb install-info*.deb
dpkg: error processing dpkg*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing install-info*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 dpkg*.deb
 install-info*.deb[/CODE]


You need to actually have these files downloaded somewhere, then run the command from the directory you downloaded the files to.

That's what the link to the package search website was for:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Later, Seeker

---

### Post by ckuecker on 2009-12-14
Rebooting safe, and trying the dpkg repair option gave similar errors. Rebooted.

Tried total removal of automake. That apparently succeeded - both automake and autoconf show up in Synaptic as uninstalled.

Tried a reinstall. The files downloaded, and I get the same bloody error - can't install automake because it depends on autoconf, which cannot be configured.

Tomorrow, I'm buying a backup hard drive and doing a Ubuntu reinstall after saving all my critical stuff.

Chuck

---

### Post by ckuecker on 2009-12-17
Now, I've got a new problem.

I installed a 500 GB Western Digital PATA drive in the machine. Had to fiddle with the BIOS settings to get it to register reliably.

It comes up as "mass storage drive" in the file browser, and is not mountable because it's not partitioned.

So, i partitioned it into four 116 GB segments, and set each up as an EXT3 file system. So far, so good.

Rebooted the system - got a slew of errors on registering that drive - and now, it's back to un-partitioned.

Anyone seen this kind of behaviour? The PC is a Pentium 3 from 2000, so possibly it needs a BIOS upgrade. Will be checking for that tonight.

Chuck

---

### Post by ckuecker on 2010-02-21
A final solution to this problem - save my home data and work data, and then install Ubuntu again. I immediately updated to 9.10, and there are no more problems.

Thanks for all the suggestions.

---


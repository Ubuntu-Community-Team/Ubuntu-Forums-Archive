---
title: "Problem upgrading from Warty"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by Bigmac on 2005-04-15
Hello all folks over here.

I'm a little new to the Ubuntu community.  It is presently my testing machine to know if I switch from Gentoo to ubuntu.  The last thing I wanted to do before the switch was a distro upgrade.

So here is the problem : I use this computer on job.  I have began the upgrade process but it fail on a package.  I have tried to correct the package with apt-get directly form the command line, but didn't find anything usefull.  Here is some of my command, that should be enough : 

```
marca@marcandre:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python2.4-pythoncard
The following NEW packages will be installed:
  python2.4-pythoncard
0 upgraded, 1 newly installed, 0 to remove and 415 not upgraded.
479 not fully installed or removed.
Need to get 0B/286kB of archives.
After unpacking 1835kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 79695 files and directories currently installed.)
Unpacking python2.4-pythoncard (from .../python2.4-pythoncard_0.8.1-1ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.4-pythoncard_0.8.1-1ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/pythoncard/pythoncard_config.txt', which is also in package python2.3-pythoncard
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-pythoncard_0.8.1-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
marca@marcandre:~ $ sudo apt-get remove python2.3-pythoncard
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-pythoncard: Depends: python2.4-pythoncard but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marca@marcandre:~ $ sudo apt-get install pythoncard
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-pythoncard: Depends: python2.4-pythoncard but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marca@marcandre:~ $ 
```

So as you can see, I can;t remove or add the proper package and that block the upgrade process.  To help, I include my /etc/apt/sources.list :

```
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb http://archive.ubuntu.com/ubuntu/ hoary main restricted  
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe  
# deb http://archive.ubuntu.com/ubuntu/ warty universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted  
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted  
```


I have tried the -m flag to apt-get, it make anything more than previously.  Since the problem is circular, can't install the pckage because of a problem, can't delete package because of a dependencies, I don't know what to do exactly.

Thanks in advance for the help you can give me.

Marc-Andre

---

### Post by Bigmac on 2005-04-15
Ok, don't know if it broke something, but with that, it seem's to make it pass and not make to much of problem : 

```
sudo dpkg -i --force-all python2.4-pythoncard_0.8.1-1ubuntu1_all.deb
```

So, hope it will help anyone...

Now have to continue the upgrade!

Thanks folk if you search for me!

---


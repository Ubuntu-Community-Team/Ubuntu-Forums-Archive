---
title: "Can't install or uninstall, please help"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2009-12-07
I'm stuck with this problem. Can't install, update or uninstall. Please help.

```

Writing extended state information... Done
(Reading database ... 241903 files and directories currently installed.)
Removing liblog4net1.2-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.1.2.log4net.installcligac
dpkg: error processing liblog4net1.2-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 liblog4net1.2-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

I also get this error message:

```
E: liblog4net1.2-cil: subprocess installed post-removal script returned error exit status 1
```

The problem appears to be a missing **policy.1.2.log4net.installcligac** file. It is referred to [here]("http://pkg-mono.alioth.debian.org/cli-policy/ch-appendix.html")in Debian CLI policy:


```
 6.1.3 dh_installcligac

dh_installcligac is used to facilitate the installation of strong-named assemblies into the various caches installed on the user's machine. Its primary purpose is to install the assemblies at the point of installation instead of pre-packing them inside the Debian package; this is also known as late-GAC install.

To identify which assemblies need to be installed into the GAC, dh_installcligac uses the debian/installcligac or the debian/packagename.installcligac to list the assemblies to install or uninstall at installation or removal respectivly.

The file format of the installcligac is simple: the full installed path of every assembly to install into the GAC. **For example, the liblog4net1.2-cil package would have this in the debian/installcligac file:**

     /usr/lib/cli/log4net-1.2/log4net.dll

dh_installcligac needs to be called after dh_install and before dh_clideps. See dh_installcligac(1) for details. 
```

How do I remove the problem? Is there a way of tricking into uninstalling?

---

### Post by chaanakya_chiraag on 2009-12-07
Have you tried
```
sudo dpkg-reconfigure liblog4net
```
If it doesn't work, please post the output dpkg-reconfigure gives you.

---

### Post by wojox on 2009-12-07
What package with mono were you install/removing ?

---

### Post by afrodeity on 2009-12-07
I installed Nant because OpenSim depended upon it. It's got to do with the .NET framework that OpenSim uses to connect its grids.

---

### Post by afrodeity on 2009-12-07
I'm really buggered

```

sudo dpkg-reconfigure liblog4net1.2-cil
/usr/sbin/dpkg-reconfigure: liblog4net1.2-cil is broken or not fully installed
afrodeity@afrodeity-desktop:/usr$ 

```

---

### Post by chaanakya_chiraag on 2009-12-07
And I presume ```
sudo aptitude purge liblog4net1.2-cil
``` doesn't work either?
[EDIT] sorry, realized that's in the original thread.

---

### Post by afrodeity on 2009-12-07
Yes, tried that also. There are some force-remove options which I need guidance on.

---

### Post by chaanakya_chiraag on 2009-12-07
GAAAAAHHHHHHH!!!!!!  I've fixed this kind of problem before, but I don't remember how!!!!!!!!!!!!

---

### Post by chaanakya_chiraag on 2009-12-07
Have you tried ```
sudo apt-get install -f
```?

---

### Post by afrodeity on 2009-12-07
Time's like these, I wish I could google people's minds, especially the people who refuse to give us an Open.NET framework alternative to mono.

---

### Post by afrodeity on 2009-12-07
```
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```

This is probably because I deleted the lock file in /var/cache/apt/archives by doing this

```


cd /var/cache/apt/archives
sudo rm -rf *
mkdir partial

```

---

### Post by chaanakya_chiraag on 2009-12-07
You should have only removed the lock file.  However, try using sudo to create the partial folder...apt wants a partial folder owned by root.

---

### Post by chaanakya_chiraag on 2009-12-07
However, the error you are getting usually refers to **having** the lock file, not deleting it :D

---

### Post by afrodeity on 2009-12-07
Yes, but I rebooted and tried apt-get install -f and get the same error

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chaanakya_chiraag on 2009-12-07
Did you try going into Synaptic Package Manager and selecting the package for removal?  That might do the --force-removal thing you were talking about earlier.  Yes, I know apt and synaptic are the same, but give it a try all the same.

---

### Post by joes7 on 2009-12-07
Download another ISO. Try by changing to Xubuntu, if you wish to install. Otherwise, format!

---

### Post by chaanakya_chiraag on 2009-12-07
[FONT=monospace]Scratch my earlier suggestion.  Try ```
sudo apt-get purge -f liblog4net1.2-cil
```
[/FONT]

---

### Post by chaanakya_chiraag on 2009-12-07
@joes7: This is not that kind of problem.  This is a problem that happens when a package is half-configured and doesn't want to install/uninstall.  This has nothing to do with variants of Ubuntu :D

---

### Post by afrodeity on 2009-12-07
In synaptic it shows up marked in red. If I try to remove I get:

E: liblog4net1.2-cil: subprocess installed post-removal script returned error exit status 1

---

### Post by afrodeity on 2009-12-07
purge -f also throws up an error 1. Should I try remove it manually? I can see the file if I do a locate:

```

afrodeity@afrodeity-desktop:~$ locate liblog4net1.2-cil
/usr/share/cli-common/packages.d/liblog4net1.2-cil.installcligac
/usr/share/cli-common/packages.d/liblog4net1.2-cil.mono
/usr/share/cli-common/policies.d/liblog4net1.2-cil
/usr/share/doc/liblog4net1.2-cil
/var/cache/apt/archives/liblog4net1.2-cil_1.2.10+dfsg-3_all.deb
/var/crash/liblog4net1.2-cil.0.crash
/var/lib/dpkg/info/liblog4net1.2-cil.clilibs
/var/lib/dpkg/info/liblog4net1.2-cil.list
/var/lib/dpkg/info/liblog4net1.2-cil.md5sums
/var/lib/dpkg/info/liblog4net1.2-cil.postinst
/var/lib/dpkg/info/liblog4net1.2-cil.postrm
/var/lib/dpkg/info/liblog4net1.2-cil.prerm

```

---

### Post by chaanakya_chiraag on 2009-12-07
Try this:[URL="http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html"]
http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html[/URL]

---

### Post by afrodeity on 2009-12-08
Following the guide suggested by chaanakya I found three postinst files set to -e. 
liblog4net1.2-cil.postrm
liblog4net1.2-cil.postinst
liblog4net1.2-cil.prerm

they each had a set -e line

I removed the line then did

sudo apt-get --purge remove liblog4net1.2-cil

Result E: File does not exist: /usr/share/cli-common/packages.d/policy.1.2.log4net.installcligac

AND sudo apt-get --purge remove liblog4net1.2-cil

Result E: File does not exist: /usr/share/cli-common/packages.d/policy.1.2.log4net.installcligac

Still stuck, but at least I'm heading in the right direction. Will investigate further and report back.

---

### Post by afrodeity on 2009-12-08
if use this sudo dpkg --force all --remove

it throws up a bunch of commands

```

afrodeity@afrodeity-desktop:/var/log$ sudo dpkg --force all --remove
dpkg: --remove needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Anyone?

---

### Post by afrodeity on 2009-12-08
Okay, I found two more guides.

[http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)

[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

But this hack worked:

[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/comment-page-1/#comment-834](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/comment-page-1/#comment-834)

This removes the offending liblog4net1.2-cil from the /var/lib/dpkg/status file. At least synaptic isn't locked up and I can install/deinstall other software by fooling the system into thinking liblog4net1.2-cil isn't installed (or in an error state). It's not ideal.

The real solution would be to fix the postinst script. I will see if I can upload them here, so that anybody who has the time and skill can determine what went wrong. 

Its a bug, because I should be able to immediately reinstall liblog4net1.2-cil via Synaptic, over-writing any file which is corrupted. The system won't let me do this, because the reinstall then again fails half-way because the install script is bad.

All three scripts related to liblog4net1.2-cil appear to be evil. I also found another script referred to by the package after opening.

 /usr/share/cli-common/policy-remove log4net 1.2 was set to -e

It would appear attempting to remove or install the package sets these scripts to -e because of policy on the system. The bug is therefore to do with conflicting policies, either on Debian/Ubuntu side, or with Mono itself. As a result, my Tomboy notes now crash. I would love to just remove Mono entirely. But then what to do about the .NET framework which is Microsoft's contribution to the Internet?

I think we would all be a lot better off demanding an OPEN .NET alternative. Removing Mono is not a solution, its a cop-out. So lesson learnt. We need to be more proactive in our activism to get Ubuntu interaction with the rest of the universe on our terms. Thanks for all the help. :)

---

### Post by afrodeity on 2009-12-08
This is the entry I removed from the dpkg status file:

```

Package: liblog4net1.2-cil
Status: deinstall ok half-installed
Priority: optional
Section: libs
Installed-Size: 352
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: log4net
Version: 1.2.10+dfsg-3
Replaces: liblog4net-cil
Depends: cli-common (>= 0.5.6), libc6 (>= 2.9) | libc6.1 (>= 2.9) | libc0.1 (>= 2.9), libmono-corlib2.0-cil (>= 1.2.2.1), libmono-system-data2.0-cil (>= 1.2.6), libmono-system-web2.0-cil (>= 1.9.1), libmono-system2.0-cil (>= 2.0)
Description: highly configurable logging API for the CLI
 log4net is a tool to help the programmer output log statements to a variety
 of output targets. log4net is a port of the excellent log4j framework to the
 Common Language Infrastructure (CLI). The framework is similar to the
 original log4j as possible while taking advantage of new features in the
 CLI runtime. For more information on log4net see the features document.
 .
 log4net is part of the Apache Logging Services project. The Logging
 Services project is intended to provide cross-language logging
 services for purposes of application debugging and auditing.
Original-Maintainer: Debian CLI Libraries Team <pkg-cli-libs-team@lists.alioth.debian.org>
Homepage: http://logging.apache.org/log4net/

```

Not pretty is it?

---

### Post by afrodeity on 2009-12-08
Here are the scripts. The set - e keeps returning.

**liblog4net1.2-cil.postrm**
```

#!/bin/sh
set -e
# Automatically added by dh_cligacpolicy
if [ "$1" = "remove" ] ||  [ "$1" = "upgrade" ] && [ -x /usr/share/cli-common/p$
        /usr/share/cli-common/policy-remove log4net 1.2
fi
# End automatically added section

```

**liblog4net1.2-cil.postinst**
```

#!/bin/sh
set -e
# Automatically added by dh_installcligac
if [ "$1" = "configure" ] && [ -x /usr/share/cli-common/gac-package-install ]; $
        /usr/share/cli-common/gac-package-install liblog4net1.2-cil
fi
# End automatically added section
# Automatically added by dh_cligacpolicy
if [ "$1" = "configure" ] && [ -x /usr/share/cli-common/policy-install ]; then
        /usr/share/cli-common/policy-install log4net 1.2
fi
# End automatically added section

```

**liblog4net1.2-cil.prerm**
```
#!/bin/sh
set -e
# Automatically added by dh_installcligac
if [ "$1" = "remove" ] || [ "$1" = "upgrade" ] && [ -x /usr/share/cli-common/ga$
        /usr/share/cli-common/gac-package-remove liblog4net1.2-cil
fi
# End automatically added section

```

---

### Post by afrodeity on 2009-12-08
This comment from Debian Admin really puts it all in a nutshel:

*...doesn't it strike anyone else that a broken package should *not* be able to paralyze the entire package system? This seems like a severe flaw with dpkg, that it can't cope with a broken package w/out resorting to the user finding the package script that is causing the breakage and editing it. And since the article is from 2005, it's not like this is a new/unknown problem.*

[http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)

---

### Post by chaanakya_chiraag on 2009-12-08
1) Does synaptic think the package is just not installed right now?
If so,
2) Have you tried manually removing the files referred to in the scripts?
- Chiraag

---

### Post by afrodeity on 2009-12-09
I think Ive solved the cause of the problem by downloading & and compiling the latest mono kit. I only had the default ubuntu libraries. Then installed the app which caused the problem & and which should have warned or downloaded dependencies -- Nant. :)

liblog4net1.2 now shows up as installed! The files will have been overwritten. However still can't launch Tomboy.

See here [http://ubuntuforums.org/showthread.php?t=1349565](http://ubuntuforums.org/showthread.php?t=1349565)

---


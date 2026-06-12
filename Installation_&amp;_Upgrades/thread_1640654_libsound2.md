---
title: "libsound2"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by hissou86 on 2010-12-08
hi,
i want to install Skype, there is a dependency problem with libsound2. When i tried to install it, this eroor had appeared to me:
```
Erro: Conflicts qith the installed package 'libsound2-plugins'
```

when i tried to install that package (libsound2-plugins), this error appeared (the same dependency problem as with skype ==> so, i am in cycle
help please
thanks a lot in advance

---

### Post by ajgreeny on 2010-12-08
What version of libsound2 and its plugins do you have installed, and do you mean libasound2?  Skype in 10.04 needs libasound2  >1.0.22 and perhaps you have an incorrect version.

---

### Post by hissou86 on 2010-12-08
Aah yes thank you
So when i began installing packages, i have faced that problem:
i wanted to install libc-bin but this error has exposed to me:
```
Embedded GNU C Library: Binaries
This package contains utility programs related to the GNU C Library.
* catchsegv: catch segmentation faults in programs
* getconf: query system configuration variables
* getent: get entries from administrative databases
* iconv, iconvconfig: convert between character encodings
* ldd, ldconfig: print/configure shared library dependencies
* locale, localedef: show/generate locale definitions
* rpcinfo: report RPC information
* tzselect, zdump, zic: select/dump/compile time zones 
```Thanks

---

### Post by hissou86 on 2010-12-09
Please, i need answer ....

---

### Post by ajgreeny on 2010-12-09
How are you trying to install skype?

Have you installed packages from places other than the standard repos that may have changed your version of libasound2 etc etc from the default versions?

The versions of libasound2 etc in the repos are the versions needed for the skype version that is in the repos, so I am surprised you are having this problem.

---

### Post by hissou86 on 2010-12-09
I downloaded the .deb skype file.
Yes i have downloaded all packages form standard repos and i have checked, all the time, the version.
One of the pachages that i neede to install was libc-bin, and i tried to install it via synaptic i faced that problem (picture attached).


Thanks

---

### Post by ajgreeny on 2010-12-09
Your problem seems to be that you have libc6 v 2.7 installed, which is much older than the normal version in Lucid, where it should be the same version as your libc-bin.  Why do you have the old libc6; any idea?

I think you should update the libc6 package, which should appear in your update-manager automatically, but presumably does not, for some reason or other.

Can I see the output of ```
cat /etc/apt/sources.list
``` please, as I suspect you may have a problem there which could account for these problems.

---

### Post by hissou86 on 2010-12-10
hi,
the libc package does not appear in my update-manager when had look at sources.list.
Besides, the versions of libc-bin and libc6 are the same (2.12.1) but the error message persist.

thanks,

---

### Post by ajgreeny on 2010-12-10
> **hissou86 said:**
> hi,
the libc package does not appear in my update-manager when had look at sources.list.
Besides, the versions of libc-bin and libc6 are the same (2.12.1) but the error message persist.

thanks,
The libc6 package will not actually appear in the sources.list file; that just points the system to the various repos.

Do you have the newer version of libc6 installed, ie 2.12.1, as the error message suggests you have 2.7.10 installed?

And are you actually still on 10.04 not 10.10, as your versions mentioned here are slightly later than those I have in 10.04  I still suspect there is something wrong with your sources, as libc6 is showing in my packages available, so can you show the output of that command I showed please, just to check.

---

### Post by hissou86 on 2010-12-10
ok 
i think that i had to note that my ubuntu version is 8.04 (i have no choice to upgrade it because this is the distribution installed by my firm technical staff).

back : 
the content of sources.list is:
```
 deb http://depot-****-test.sst.****/ ****-socle01 main
 deb http://depot-****-socle02.sst.****/ ****-socle02 main
 deb http://depot-****-hardy.sst.****/ hardy main restricted universe multiverse
 deb http://depot-****-hardy.sst.****/ hardy-updates main restricted universe multiverse
 deb http://depot-****-hardy.sst.****/ hardy-security main restricted universe multiverse
 deb http://depot-outils-****.sst.****/ outils-**** main
 deb http://depot-****-socle03.sst.****/ ****-socle03 main
 deb http://apt.wicd.net/ jaunty extras
 deb http://www.backports.org/debian lenny-backports main contrib non-free
 deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse restricted universe main
 deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype

```

sorry, i think that i must'n show the name of the company.
i appreciate your help
thanks,

---

### Post by ajgreeny on 2010-12-10
Your profile shows 10.04, but now you say you are running 8.04; which is it?  There is a very good site which allows you to generate your ideal sources.list file with a few clicks of the mouse, depending on what specific repos you want, ie which restricted packages are allowed.

Have a look at this and see if it helps you at all, as your current sources.list is so customised I don't know quite what to tell you to add or remove.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by hissou86 on 2010-12-11
thanks; it's so helpful

---


---
title: "How do I fix broken packages?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by fredxor on 2007-03-04
I had the misfortune of breaking packages while installing some .deb packages. The packages that are broken are: cpp-4.1, gcc-4.1, libgcc1, libstdc++6. In the Synaptic Package Manager, I have tried to reinstall them, but that means that I have to uninstall a ton of other packages. After choosing to reinstall the 4 broken packages, I get this error:
> Could not apply changes!
Fix broken packages first.

I have no idea what to do now. There seems to be no way that I can reinstall the broken packages or fix them. Please help!

Thankyou,
    freddy

---

### Post by Jussi Kukkonen on 2007-03-04
Synaptic probably gives you no tools to handle that...

*man apt-get* will show you that using the *--fix-broken* flag with *apt-get install* may help

---

### Post by fredxor on 2007-03-04
When I try to fix the broken packages, I get this output:
```
chris@mars:~$ sudo apt-get install --fix-broken
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I downloaded the gcc-4.1-base deb package for Edgy, but I get this when I open it:
> Broken dependencies
Your system has broken dependencies. This application can not continue until this is fixed. To fix it run 'sudo synaptic' or 'sudo apt-get install -f' in a terminal window.

When I try to do what it asks, it gives me this:
```
chris@mars:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

---

### Post by fredxor on 2007-03-04
I just tried going into Synaptic and clicking Edit->Fix Broken Packages. It tells me that an error occurs and gives me this output:
> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Please help!

Thanks,
    freddy

---

### Post by Jussi Kukkonen on 2007-03-05
This should give you a clean repository version of gcc-base:
> sudo apt-get clean
sudo apt-get install --reinstall gcc-4.1-base

---

### Post by fredxor on 2007-03-05
Thanks for the help. Unfortunately, you suggestion did not work :( .
```
chris@mars:~$ sudo apt-get clean
Password:
chris@mars:~$ sudo apt-get install --reinstall gcc-4.1-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of gcc-4.1-base is not possible, it cannot be downloaded.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is to be installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is to be installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is to be installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Jussi Kukkonen on 2007-03-06
> Reinstallation of gcc-4.1-base is not possible, it cannot be downloaded.
Sounds like the problem is your repository list then, although the exact error message is new to me... As you can see [here]("http://packages.ubuntu.com/edgy/libs/gcc-4.1-base"), that package is available for edgy (which I presume your are using). 

Can you paste the contents of */etc/apt/sources.list*, please?

---

### Post by Tdrtnlz on 2007-03-08
Just Googling to find an answer to my problem, I came across this thread, and what fredxor is describing is exactly the same as what I am suffering from.

After trying all of the commands that Jussi Kukkonenposted, I also get the same outputs in the terminal.

Here is the contents of my /etc/apt/sources.list:
```
deb file:/var/cache/apt-build/repository apt-build main

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://flomertens.keo.in/ubuntu edgy main main-all
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
deb http://ubuntu.beryl-project.org/ edgy main
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
deb http://ubuntu.beryl-project.org/ edgy main
deb http://ubuntu.beryl-project.org edgy main
deb http://ubuntu.beryl-project.org edgy main

```

Please note that I have only been using Ubuntu and Linux for about a week, and up until now, have experienced very few problems, so any help would be greatly appreciated.

Thanks in Advance.

EDIT: 
I think I have fixed this problem by downgrading gcc-4.1-base by typing the following in the terminal:
```
sudo aptitude purge gcc-4.1-base
```
It now shows no broken packages in Synaptic, and new packages can be installed without the previous error messages showing up.

---


---
title: "Unable to upgrade the server due to python and lgtoclnt"
date: 2021-08-18
forum: Installation &amp; Upgrades
---

### Post by devopsall90 on 2021-08-18
Hi All,

I ve 2 devices which are running on below version and while doing the upgrade there are dependencies which is not been supported and not allowing for further upgrade.


**OS Version	Ubuntu 16.04.7 LTS**


Dependencies
#apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
apport : Depends: python3-apport (>= 2.20.1-0ubuntu2.30) but 2.20.1-0ubuntu2.19 is installed
python3-pip : Depends: python-pip-whl (= 8.1.1-2ubuntu0.4) but 8.1.1-2ubuntu0.6 is installed
ubuntu-release-upgrader-core : Depends: python3-distupgrade (= 1:16.04.32) but 1:16.04.26 is installed
ubuntu-server : Depends: motd-news-config but it is not installed
update-manager-core : Depends: python3-update-manager (= 1:16.04.17) but 1:16.04.15 is installed
E: Unmet dependencies. Try using -f.




**OS Version: Ubuntu 16.04.6 LTS**
# apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
ciscoampconnector : Depends: libc6 (>= 2.29) but 2.23-0ubuntu11.2 is installed
                     Depends: libgcc-s1 (>= 3.3) but it is not installable
                     Depends: libpcre2-8-0 (>= 10.22) but it is not installed
                     Depends: libstdc++6 (>= 9) but 5.4.0-6ubuntu1~16.04.12 is installed
                     Depends: libtinfo6 (>= 6) but it is not installable
lgtoclnt : Depends: ksh but it is not installed or
                     pdksh but it is not installable
E: Unmet dependencies. Try using -f.


Also tried to fixed with multiple ways

apt-get -f install
apt install --fix-broken
apt install reinstall python-minimal
apt update
apt-get upgrade -f

dpkg configure -a
dpkg --get-selections | grep "hold"
apt remove


But unfortunately unable to proceed further with the upgrade, please recommend.

---

### Post by deadflowr on 2021-08-18
16.04 has reached end of life,
but for curiosity sake, Please post the output for 
```
sudo apt update
```

---

### Post by TheFu on 2021-08-18
16.04 support ended in April.  BEFORE that time and the repos have been moved to ESM.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)
If you cannot update today, pay for ESM support for the few more years (i.e. stay on 16.04) as you and your boss comes up with a plan to migrate all the applications to supported Linux releases.

If you have the skills to port the code, you can do that.  I ported my backup tool version so it would run on 20.04.  I was lucky in that only a few dependencies needed to be ports and those didn't have more dependencies.  I'd rather run the newer version of the backup tool across all my different systems, but there are other limitations holding those systems back.  Fortunately, I'm not on 16.04 anymore. The migration to 18.04 wasn't tool painful for us.  20.04 - well, that was too hard for some of our systems.  Our email communications server hasn't been ported to 20.04 yet by the commercial vendor. In the past, it took them a year after an LTS release before it was supported. I haven't checked in the last month if they've go a 20.04 version out.  I'd rather migrate on my schedule, then being forced.

You can run the different applications in either a VM just for it or in a container with the specific dependencies.  A container would have higher risks, but are usually 10-100 less overhead than a full VM.  For the last 15 yrs, nobody should be deploying applications directly on hardware anyways. Always virtualize or use a container.

---

### Post by MAFoElffen on 2021-08-18
You have your posted command as a typo... should be 
```
sudo apt install -f
```

On your post. please go back and edit it to wrap your output within [noparse]```
 insert_output_here 
```[/noparse] tags...

Here is what I see
```
# apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
ciscoampconnector : Depends: libc6 (>= 2.29) but 2.23-0ubuntu11.2 is installed
                     Depends: libgcc-s1 (>= 3.3) [COLOR=#ff0000]but it is not installable[/COLOR]
                     Depends: libpcre2-8-0 (>= 10.22) but it is not installed
                     Depends: libstdc++6 (>= 9) but 5.4.0-6ubuntu1~16.04.12 is installed
                     Depends: libtinfo6 (>= 6) [COLOR=#ff0000]but it is not installable[/COLOR]
lgtoclnt : Depends: ksh but it is not installed or
                     pdksh [COLOR=#ff0000]but it is not installable[/COLOR]
E: Unmet dependencies. Try using -f.

```
Did doing 
```
sudo apt install -f
```
Correct that?

If not, those errors are telling you that your GCC compiler is out of date, needs to be upgraded or resynced/reinstalled...

Please post...
```
gcc -version
apt-cache show gcc
```

**[COLOR=#ff0000]EDITED: SEE MY NEXT POST...[/COLOR]**

---

### Post by TheFu on 2021-08-18
But all those repos have been moved, so how will the OP install anything?

---

### Post by MAFoElffen on 2021-08-18
[COLOR=#ff0000]Wait...[/COLOR] 

Deb package "ciscoampconnector" is straight from Cisco and is manually installed. It is also well past it's supported end of life. The current version from Cisco is only supported for Ubuntu 20.04.

And package "lgtoclnt" is also a manually installed old networking tool...

The updated solution would be to remove both of those... Do your updates to current > Do release upgrades to get it to a supported LTS version... then decide if you really need to reinstall those tools... Things have changed over the years and there are many modern networking toolsets that are here now.

[COLOR=#ff0000]Note:[/COLOR] if he is not getting errors on apt update, then his sources list is pointing to the old archive repo's...

---

### Post by devopsall90 on 2021-08-19
Hi,

I want to remove the cisco package from the server without any dependencies but it still reflects with the same. 

# gcc --version
gcc (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

###################################################################
#apt-cache show gcc
Package: gcc
Priority: optional
Section: devel
Installed-Size: 44
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-defaults (1.150ubuntu1)
Version: 4:5.3.1-1ubuntu1
Provides: c-compiler
Depends: cpp (>= 4:5.3.1-1ubuntu1), gcc-5 (>= 5.3.1-3~)
Recommends: libc6-dev | libc-dev
Suggests: gcc-multilib, make, manpages-dev, autoconf, automake, libtool, flex, bison, gdb, gcc-doc
Conflicts: gcc-doc (<< 1:2.95.3)
Filename: pool/main/g/gcc-defaults/gcc_5.3.1-1ubuntu1_amd64.deb
Size: 5244
MD5sum: 
SHA1: 
SHA256: 
Description-en: GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C.
 .
 This is a dependency package providing the default GNU C compiler.
Description-md5: 
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Build-Essential: yes
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, edubuntu-desktop, edubuntu-usb, xubuntu-core, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntu-gnome-desktop, ubuntukylin-desktop


#######################################################################



Kindly let me know your inputs.

---

### Post by MAFoElffen on 2021-08-19
Hmmm...14.04 Server Edition (That's what you said in last post)... Do you have aptitude installed?

If so, remove those from there, so that aptitude can resolve the dependencies.

If not then via dpkg:
```
sudo dpkg -r <application_name>
```

Since those two packages are 3rd party and not Repo packages, I do not feel that apt-get can do anything with them.

---


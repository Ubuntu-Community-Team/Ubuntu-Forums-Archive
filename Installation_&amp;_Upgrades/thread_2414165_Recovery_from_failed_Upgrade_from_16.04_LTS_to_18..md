---
title: "Recovery from failed Upgrade from 16.04 LTS to 18.04 LTS dpkg errors."
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-03-06
OK, I'm on my 4th of 7 upgrades from 16.04 to 18.04. 2 went well 2 went not so well. 

The one I working on now went not so well as somewhere a number of packages failed to download and configure leaving me with a partially working system,. I've not got the computer almost working except I can't run ```
# apt upgrade
```  or ```
# dpkg --configure -a
``` or```
 # apt autoremove
``` because of dpkg errors that seem to be caused by conflicts between different packages that seem to be very similar.

Here is some output

```
# dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-45-generic:
 linux-tools-4.15.0-45-generic depends on linux-tools-4.15.0-45; however:
  Package linux-tools-4.15.0-45 is not installed.

dpkg: error processing package linux-tools-4.15.0-45-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-43-generic:
 linux-tools-4.15.0-43-generic depends on linux-tools-4.15.0-43; however:
  Package linux-tools-4.15.0-43 is not installed.

dpkg: error processing package linux-tools-4.15.0-43-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-tools-4.15.0-45-generic
 linux-tools-4.15.0-43-generic
root@Henry:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-45-generic:
 linux-tools-4.15.0-45-generic depends on linux-tools-4.15.0-45; however:
  Package linux-tools-4.15.0-45 is not installed.

dpkg: error processing package linux-tools-4.15.0-45-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-tools-4.15.0-43-generic:
 linux-tools-4.15.0-43-generic depends on linux-tools-4.15.0-43; however:
  Package linux-tools-4.15.0-43 is not installed.

dpkg: error processing package linux-tools-4.15.0-43-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-tools-4.15.0-45-generic
 linux-tools-4.15.0-43-generic 
```

I'm not sure why I have two versions of linux-tools trying to be installed.

whne I run 
```
# apt install -f 
```
Part of the output is this:

```
The following additional packages will be installed:
  linux-tools-4.15.0-43 linux-tools-4.15.0-45
The following NEW packages will be installed:
  linux-tools-4.15.0-43 linux-tools-4.15.0-45
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,212 kB of archives.
After this operation, 41.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 313063 files and directories currently installed.)
Preparing to unpack .../linux-tools-4.15.0-43_4.15.0-43.46_amd64.deb ...
Unpacking linux-tools-4.15.0-43 (4.15.0-43.46) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.15.0-43_4.15.0-43.46_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.15.0-43', which is also in package linux-hwe-tools-4.15.0-43 4.15.0-43.46~16.04.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../linux-tools-4.15.0-45_4.15.0-45.48_amd64.deb ...
Unpacking linux-tools-4.15.0-45 (4.15.0-45.48) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.15.0-45_4.15.0-45.48_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.15.0-45', which is also in package linux-hwe-tools-4.15.0-45 4.15.0-45.48~16.04.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-4.15.0-43_4.15.0-43.46_amd64.deb
 /var/cache/apt/archives/linux-tools-4.15.0-45_4.15.0-45.48_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This seems to indicate ```
linux-hwe-tools-4.15.0-43 4.15.0-43.46~16.04.1
```is already installed.
So the question is should I remove the partially installed packages and hope for the best?

---

### Post by Bashing-om on 2019-03-06
rsteinmetz70112; Hello -

I get this ball started rolling.
The question is why did not the kernels fully install ?
what shows for a "out of disk space" possibility ?
```

df -h
df -i

```

and next we need to know what kernels are installed:
```

sudo dpkg -l | grep linux-
ls -al /boot/

```

The current 18.04 kernel is:
> 
sysop@x1804mini:~$ uname -r
4.15.0-46-generic
sysop@x1804mini:~$


[INDENT]see what story gets told
[/INDENT]

---

### Post by rsteinmetz70112 on 2019-03-08
The kernel did fully install and the computer boots. During the upgrade something went wrong and a lot of packages weren't configured because some packages didn't install. I fixed much of that with dpkg but now I can't update or upgrade because of the dependency problems.

There is plenty of disk space.

I think the three versions of linux-tools are in conflict, and I'm not sure which one or ones I need.
```
linux-hwe-tools-4.15.0-43 (installed)
linux-tools-4.15.0-45 (not installed)
linux-tools-4.15.0-43 (not installed)
```
If the Linux-hwe-tools-4.15.0.43 is an equivalent alternative to the other two I may be fine.

These two packages won't install
```
linux-tools-4.15.0-45-generic
linux-tools-4.15.0-43-generic
```
It looks to me like -45 package should supersede the -43 package and I shouldn't need both.
But I'm in unfamiliar territory.

I suppose I could remove the two  -generic packages and see if the resolves the issue.
But I am concerned that will break something else, so I'm being careful.

Potential commands to remove the packages are:
```
# apt <remove>
```
or
```
# dpkg -remove <package>
```
or
```
 dpkg -purge <package>
```

---

### Post by Impavidus on 2019-03-08
linux-hwe-tools-4.15.0-43 is a leftover from 16.04. It should have been removed during the release upgrade. The other packages belong to 18.04.

---

### Post by rsteinmetz70112 on 2019-03-08
I'll try to remove and install it then.

I'll see if I can do it on the running system or if I have to do it in a chroot session, after downloading the correct packages.

---

### Post by rsteinmetz70112 on 2019-03-11
If this should have been upgraded and for some reason wasn't is there a way to upgrade or replace a single package?

It seems this error seems to be saying dpkg can't overwrite a file :
```
dpkg: error processing archive /var/cache/apt/archives/linux-tools-4.15.0-43_4.15.0-43.46_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.4.15.0-43', which is also in package linux-hwe-tools-4.15.0-43 4.15.0-43.46~16.04.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
```

---

### Post by Impavidus on 2019-03-11
Have you tried to remove it with```
sudo dpkg --purge linux-hwe-tools-4.15.0-43
```

---

### Post by rsteinmetz70112 on 2019-03-11
Not yet. It's at another site and I won't be there again until till next week. Fortunately it's not a production system and I can afford to wait on this one.

I am a little concerned that if I try to remove it with dpkg it will break a lot of dependencies.

I also don't understand if it's been replaced why won't the new package simply install over it. 

I did find this thread
[https://askubuntu.com/questions/539235/how-to-remove-obsolete-packages-after-failed-release-upgrade-via-do-release-upgrade](https://askubuntu.com/questions/539235/how-to-remove-obsolete-packages-after-failed-release-upgrade-via-do-release-upgrade)

---

### Post by mtodorov69 on 2019-03-13
> **rsteinmetz70112 said:**
> Not yet. It's at another site and I won't be there again until till next week. Fortunately it's not a production system and I can afford to wait on this one.

I am a little concerned that if I try to remove it with dpkg it will break a lot of dependencies.

I also don't understand if it's been replaced why won't the new package simply install over it. 

I did find this thread
[https://askubuntu.com/questions/539235/how-to-remove-obsolete-packages-after-failed-release-upgrade-via-do-release-upgrade](https://askubuntu.com/questions/539235/how-to-remove-obsolete-packages-after-failed-release-upgrade-via-do-release-upgrade)

Am I wrong, or have you forgotten the
```
# apt update
```
after changing the repositories in /etc/apt/sources.list ?

---

### Post by rsteinmetz70112 on 2019-03-14
> **mtodorov69 said:**
> Am I wrong, or have you forgotten the
```
# apt update
```
after changing the repositories in /etc/apt/sources.list ?

I can try again, and check it but I'm pretty sure I've run ```
apt upgrade
``` and apparently it marked the need to install the packages but when I run```
 apt upgrade
``` or```
 dpkg --configure
``` it fails due to dependency issues. I can't install the packages ```
apt upgrade
``` has downloaded, because of the dependency issues.

I found this thread which may hold some clues:

[https://askubuntu.com/questions/351703/installing-a-local-package-to-replace-an-already-installed-one](https://askubuntu.com/questions/351703/installing-a-local-package-to-replace-an-already-installed-one)

---

### Post by rsteinmetz70112 on 2019-03-20
Thanks everyone who contributed. I think I've solved it.

I had to purge the original package with :
```
# dpkg --purge linux-hwe-tools-4.15.0-43
```
That left some dependency problems so I had to:
```
# dpkg --purge linux-hwe-tools-4.15.0-45
```
I was then able to run:
```

# apt -f install
# dpkg --configure -a
# apt update
# apt upgrade
```

Time to reboot and see if it works

---


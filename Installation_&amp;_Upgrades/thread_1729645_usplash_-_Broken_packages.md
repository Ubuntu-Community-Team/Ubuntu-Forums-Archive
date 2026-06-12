---
title: "usplash - Broken packages?"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by doctortonic on 2011-04-15
wolfy@Stardust:~$ sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
 procps : Depends: upstart-job
          Depends: initscripts but it is not going to be installed
 usplash : Depends: upstart-job
           Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
 xfwm4 : Depends: libstartup-notification0 (>= 0.10) but it is not going to be installed
         Depends: libwnck22 (>= 2.22.0) but it is not going to be installed
         Depends: libxfcegui4-4 (>= 4.6.0) but it is not going to be installed
         Depends: libxfconf-0-2 but it is not going to be installed
         Recommends: xfwm4-themes but it is not going to be installed
E: Broken packages
wolfy@Stardust:~$

---

### Post by Frogs Hair on 2011-04-15
What version of Ubuntu ? I just installed from the software  center on Ubuntu 10.10 , but I don't know if it will work . I installed to check for dependency problems.

---

### Post by doctortonic on 2011-04-15
same, 10.10 aka maverick. But I have another problem to.

after sudo update-alternatives --config default.plymouth
I select another bootscreen like xfce or ubuntu, or ubuntu studio and remain's the kubuntu bootscreen.

---

### Post by Frogs Hair on 2011-04-15
> **doctortonic said:**
> same, 10.10 aka maverick. But I have another problem to.

after sudo update-alternatives --config default.plymouth
I select another bootscreen like xfce or ubuntu, or ubuntu studio and remain's the kubuntu bootscreen.

I don't think that application works for changing boot-splash screens on the latest versions of Ubuntu.

---

### Post by doctortonic on 2011-04-15
1.I reinstalled Ubuntu Maverick Again. It;s fresh, Original Configurations. 
2.Bring the system up-to-date with update manager from system-administration.
3.Tried to install usplash -NO SUCCES!

```
wolfy@Stardust:~$ sudo apt-get install usplash
[sudo] password for wolfy: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wolfy@Stardust:~$ sudo apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
 libmicroblog4 : Depends: libkpimutils4 (= 4:4.5.1-0ubuntu1) but it is not going to be installed
 procps : Depends: upstart-job
          Depends: initscripts but it is not going to be installed
 usplash : Depends: upstart-job
           Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
E: Broken packages
wolfy@Stardust:~$uname -a
Linux Stardust 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
wolfy@Stardust:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
wolfy@Stardust:~$ 
 
```

---


---
title: "acpi failure after upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Merritt.kr on 2007-10-21
Had a bit of a rocky upgrade process.

Right now I'm having one problem:

```
ldconfig deferred processing now taking place
Setting up acpid (1.0.4-5ubuntu8) ...
Loading ACPI modules....
Starting ACPI services...invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Not sure how to fix this.

I wasn't able to use the "upgrade tool" for most of the Gutsy upgrade - kept crashing my computer. Had to download most from the Adept Updater after the update tool crashed. I'm not sure if my gutsy is all proper and whatnot, if that makes any sense, though it says it has all but one package (which won't install, doesn't say what it is?) and the new kernel is working.

Kubuntu Gutsy (hopefully)
Dell Inspiron 6400
ATI x1400



Thank you in advance for any help or advice! :)

---

### Post by ram100987 on 2007-10-21
i have the same issue as you with acpi.... still working on getting it to work right though

---

### Post by yzf600 on 2007-10-21
I also have the same issue with the acpi package failing and causing dependant packages to fail: I have 4 that fail:

acpid
acpi-support
powermanagement-interface
ubuntu-desktop


My gui install froze on a "waiting for xfont server to shutdown" message. I did a soft-reboot (ctl-alt-del) and was forced to do the rest of the upgrade via command line "sudo apt-get dist-upgrade". 

I can successfully boot the new kernel (that is after I booted the old kernel and deleted the evms package that hosed the new kernel up). 

I'm still looking into solving the acpi issue.

---

### Post by Ed.Corcoran on 2007-10-22
I'm also having the same problem. I'm running a Dell Latitude C400 laptop with Ubuntu & Xubuntu on it. 

```

ed@ed-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 xubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
 xubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Here's what Update Manager gives me
```

E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: xubuntu-desktop: dependency problems - leaving unconfigured

```

---

### Post by Merritt.kr on 2007-10-22
At least I am not the only one to be having this problem. Still haven't found a way to fix it myself, anyone out there have suggestions for us poor folks with broken power management?

---

### Post by yzf600 on 2007-10-22
I found the solution:

```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a

```

[http://ubuntuforums.org/showthread.php?p=3567324](http://ubuntuforums.org/showthread.php?p=3567324)

---

### Post by Merritt.kr on 2007-10-23
That worked like a charm. Thank you for the tip! :)

---

### Post by MrLizard on 2007-11-08
man, that's helpful...

---

### Post by aattila on 2007-11-10
Hey yzf600, I had the same problem, but it worked! Great! Thank you!

---

### Post by schnook9 on 2007-12-19
holy wow, that worked!!  I had kdebluetooth and wvdial still to upgrade after that, and apt-get dist-upgrade kept telling me 2 more to do, but i won't do them.... so I just did an apt-get install on the 2 packages and they went golden.  
Thanks so much for the help yzf600!

---

### Post by bcalder01 on 2008-01-08
Thank you sir!! How helpful is that??!!

---

### Post by lmc on 2008-02-05
wow. you are a genius. thanks :)

---


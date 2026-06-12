---
title: "Ubuntu 11.10 failing to upgrade"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by the_blue_box on 2012-07-07
Hi everyone, I've got a bit of a of a problem with my install of Ubuntu 11.10 (that I haven't used in a while) in that is whenever I try to upgrade it to 12.04 I will get to...
```
setting new software channels
```

then gives

```
Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.
```

I think it has something to do with the linux-image not being up to date but I'm not sure

Any help would be much appreciated!

Thanks

---

### Post by cdoebbler on 2012-10-20
I am trying to upgrade 11.10 to 12.04 but I just can't get my 11.10 to recognize that there is a new release (12.04) to which to upgrade. Any help welcome. Attaching the following from Terminal:

x:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric


x:~$ sudo apt-get dist-upgrade
[sudo] password for x: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


x:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found


x:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found

---


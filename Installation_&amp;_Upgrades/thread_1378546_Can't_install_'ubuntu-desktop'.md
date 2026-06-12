---
title: "Can't install 'ubuntu-desktop'"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by andypi on 2010-01-11
When I try and update (or when Ubuntu automatically tries to update), I first get the error "Not all upgrades can be installed". This error message gives me the option to do a "Partial Upgrade". However, when I click this the upgrade dialog hangs for quite a while before giving me the error "Can't install 'ubuntu-desktop'. It was impossible to install a required package. Please report this as a bug." When this error is dismissed I am finally given this error:

"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'update-manager' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later"

before the upgrader exits.

Could anyone tell me how to find out what the problem is here?

Thanks.

---

### Post by oldos2er on 2010-01-11
Which version of Ubuntu are you running?

---

### Post by andypi on 2010-01-11
Sorry, I should have put that in. I'm on Karmic.

---

### Post by wscrivens on 2010-01-14
I'm having exactly the same problem.  I get a dialog box:
```

Update-Manager
Can't install 'ubuntu-desktop'
It was impossible to install a required package. Please report this as a bug. 

```
Then I see the message about removing update-manager.

I went to bugzilla but could not find an appropriate categour to enter this, so I came here instead.

I've never run a pre-release version of Ubuntu, and I have installed nmap by compiling from source rather than using the package manager.
I could use some guidance in reading the log files in /var/log/installer - maybe there will be a clue there?  I did find the following in casper.log - maybe it's useful?\```

Found label 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'

```
Help, Please!

Walt

---

### Post by andypi on 2010-01-14
Hi. I'm afraid I'm now running Ubuntu from a flash drive, and my efforts have not been successful. I'm currently in the process of backing up and staring fresh :-(

Andy

---

### Post by Sef on 2010-01-14
> This is most likely a transient problem, please try again later"

It would be best to wait and see if this problem gets fixed within the next few days.    Also have you reported it or checked to seen it was reported?

---

### Post by andypi on 2010-01-14
I tried to report it, but was told that the package in question was not part of Ubuntu and could not be reported. Ultimately I used aptivate to do the upgrade which fixed that package but left me with two new dependency issues, and now Ubuntu won't boot. I am also unable to fix the dependency issues by chrooting into my installation and can only assume that the package has come from a different repository on or something. Anyway, now that I have a non-functioning system, I'd rather reinstall than wait a few days.

Thanks anyway.

Andy

---

### Post by sb92075 on 2010-01-16
I recently upgrade & am seeing similar issues 
below is grepped fro apt.log

ERROR:root:Installing/upgrading 'ubuntu-minimal' failed
ERROR:root:Installing/upgrading 'ubuntu-standard' failed
ERROR:root:failed to mark 'ubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)
ERROR:root:Dist-upgrade failed: 'The package 'update-manager' is marked for removal but it is in the removal blacklist.'

Any advice on how to correct these errors would be appreciated.

---

### Post by sandos on 2010-02-05
Also seeing this when trying to upgrade from Karmic to Lucid Lynx. Apparently a similar bug was fixed previously:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/492215](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/492215)

---


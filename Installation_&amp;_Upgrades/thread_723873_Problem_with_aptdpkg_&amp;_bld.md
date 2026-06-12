---
title: "Problem with apt/dpkg &amp; bld"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by sinister porpoise on 2008-03-13
This is what I get when running dselect-upgrade

After this operation, 3125kB disk space will be freed.
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 338395 files and directories currently installed.)
Removing bld ...
Stopping Black List Daemon: invoke-rc.d: initscript bld, action "stop" failed.
dpkg: error processing bld (--remove):
 subprocess pre-removal script returned error exit status 1
chown: cannot access `/var/run/bld': No such file or directory
Starting Black List Daemon: bld.
Errors were encountered while processing:
 bld
E: Sub-process /usr/bin/dpkg returned an error code (1)


It doesn't matter if I try to force install, removal, purge, dselect-upgrade, whatever with bld. It errors out on me. :mad:

---

### Post by sinister porpoise on 2008-03-14
ian@ian-laptop:~$ sudo dpkg --force-all --remove bld
(Reading database ... 338395 files and directories currently installed.)
Removing bld ...
Stopping Black List Daemon: invoke-rc.d: initscript bld, action "stop" failed.
dpkg: error processing bld (--remove):
 subprocess pre-removal script returned error exit status 1
chown: cannot access `/var/run/bld': No such file or directory
Starting Black List Daemon: bld.
Errors were encountered while processing:
 bld

---

### Post by sinister porpoise on 2008-03-14
Anyone? I can't update my system until this is fixed :confused:

---

### Post by sinister porpoise on 2008-03-18
> **sinister porpoise said:**
> Anyone? I can't update my system until this is fixed :confused:

e

---

### Post by mopp4 on 2008-03-19
On my box i ran this command :

```
sudo dpkg --configure -a

```
and the problem just went away......but when i remote into my daughters Edubuntu system, when ever i go to updrage or install another package i get the same dpkg error with  ubuntu-docs. 

I hope this helps. Any suggestions for my issue?

---

### Post by sinister porpoise on 2008-03-22
> **mopp4 said:**
> On my box i ran this command :

```
sudo dpkg --configure -a

```
and the problem just went away......but when i remote into my daughters Edubuntu system, when ever i go to updrage or install another package i get the same dpkg error with  ubuntu-docs. 

I hope this helps. Any suggestions for my issue?

Doesn't fix for me :confused:

---


---
title: "Update-manager Stuck"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by jackn on 2007-08-22
When I run update-manager off the desktop icon, it gets stuck.

It displays 'preparing packages' and just thrashes forever. I have to kill it from the command line.

This has happened several times, which means that I cannot at this point install the updates in question. I might not be able to install future ones, either, for all I know.

I've tried to run the packages listed using aptitude from the command line. Here i got more info:

```
The following packages will be upgraded:
  libjasper-1.701-1 libjasper-1.701-dev 
2 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/762kB of archives. After unpacking 16.4kB will be freed.
Do you want to continue? [Y/n/?] y
(snipped)
Parsing Found/Fixed information... Done
**_grave bugs_** of libjasper-1.701-1 (1.701.0-2 -> 1.701.0-2ubuntu0.7.04) <done>
 #413041 - jasper: Heap corruption on malformed image input. (Fixed: jasper/1.900.1-3)
Summary:
 libjasper-1.701-1(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]
```

I got essentially the same message when I tried to install an rsync upgrade, another package featured in update-manager's list.

In both cases, I said 'no', so I still have the update star on the desktop, beckoning for me to install updates.

What's going on?

Thanks, 
jackn

---

### Post by zparihar on 2007-08-22
I'm getting the exact same issue when i do a 'sudo aptitude upgrade' 

Does anyone know if this means that aptitude is telling me that there is a bug in this/these package(s) or if these are bug-fixes for these packages.

Here is the output

> 
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
grave bugs of libjasper-1.701-1 (1.701.0-2 -> 1.701.0-2ubuntu0.7.04) <done>
 #413041 - jasper: Heap corruption on malformed image input. (Fixed: jasper/1.900.1-3)
serious bugs of rsync (2.6.9-3ubuntu1 -> 2.6.9-3ubuntu1.1) <done>
 #438125 - CVE-2007-4091 off-by-one in sender.c (Fixed: rsync/2.6.9-5)
Summary:
 rsync(1 bug), libjasper-1.701-1(1 bug)


Until I find out what this means, i will refrain from upgrading these packages.

Thanks for your help.

Zubin Parihar

---

### Post by zparihar on 2007-08-22
Hey Jackn

I just found at that the output we got from the update is a result of an installed package called 'apt-listbugs'.  This basically is a package that lists critical bugs before each apt installation

so... when it says:

> serious bugs of rsync (2.6.9-3ubuntu1 -> 2.6.9-3ubuntu1.1) <done>
 #438125 - CVE-2007-4091 off-by-one in sender.c (Fixed: rsync/2.6.9-5)

it says that rsync version 2.6.9-3ubuntu1 contained a bug which is actually listed bugs.debian.org which is referenced by #438125 - CVE-2007-4091 .

It also says that it is installing rsync version 2.6.9-5 which is the bugfixed version.

If you do not want any of these messages anymore all you need to do is remove the package 'apt-listbugs' by running:


```
sudo aptitude remove apt-listbugs
```

Zubin Parihar

---


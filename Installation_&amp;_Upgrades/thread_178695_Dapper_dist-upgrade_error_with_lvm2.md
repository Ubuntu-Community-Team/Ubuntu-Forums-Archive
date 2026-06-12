---
title: "Dapper dist-upgrade error with lvm2"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by kh4nh on 2006-05-18
Hi guys,

I was doing dist-upgrade on my machine running Dapper and got this error. I was wondering if this is a bug. Anyone got the same problem as me?

```
root@ubuntu:/home/kh4nh# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be upgraded:
  lvm2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
Need to get 0B/279kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 91383 files and directories currently installed.)
Preparing to replace lvm2 2.01.15-0ubuntu4 (using .../lvm2_2.02.02-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/kh4nh#

```

---

### Post by nalle on 2006-06-02
I have the same problem, upgrading with the alternate ubuntu -iso. 

The problem seems to be that there is no ubuntu-base anymore, but lvm2 requires it. You can install other packages simply by unselecting it.

After rebooting I also have no sound, internet or USB, I don't know if those are affected by not having lvm2.

Any ideas on how to fix it?

t.v

---

### Post by nalle on 2006-06-02
I fixed the problem by removing ubuntu-standard, which needed the lvm2. 

The other problems that I had were nonrelated, I fixed those as well and dapper is working as it should. Nice distro :) 

Hope that helps anyone with the same problem

t.v

---

### Post by bertrand82 on 2006-06-09
I have exactly the same problem, lvm2 refuses to install, and I do not have sound or USB either. How did you fix the problem?

Thank you very much!

---

### Post by turnovg on 2006-06-10
I got the same error. But I fixed it.
   First - I unmounted my non Ubuntu partitions.
   Second - I deinstalled the previous version of lvm2 :) Like this:

sudo apt-get remove --purge lvm2...(version)

   And reinstalled the new from the apt cache archive directory.

   This worked. If not, you could try to aptitude as well.


P.S.
I've been upgrading since Ubuntu 5.04. To 5.10 some months ago and to 6.06 now.

P.S.2
My eth0 disappeared, but, it seems, solving the lvm2 problem fixed the things.

---

### Post by jeffvc on 2006-07-11
If anyone is still having this problem, this has been reported as a bug on Launchpad.  The solution to this problem is contained within the thread:

[https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972/](https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972/)

A summary follows:

The best solution is to put lvm2 on hold:

```
aptitude hold package_name
```

If you've already removed lvm2, you will need to remove or comment out the following lines in the preinst file:

```
if ! dpkg --compare-versions $(uname -r) ge '2.6.12'; then
 db_fset lvm2/kernel seen false
 db_input critical lvm2/kernel || true
 db_go
 exit 1
fi
```

Then rebuild and install the deb.  This is what I had to do.

---

### Post by fortran01 on 2006-07-13
Where is the preinst file?

> **jeffvc said:**
> If you've already removed lvm2, you will need to remove or comment out the following lines in the preinst file:

```
if ! dpkg --compare-versions $(uname -r) ge '2.6.12'; then
 db_fset lvm2/kernel seen false
 db_input critical lvm2/kernel || true
 db_go
 exit 1
fi
```

Then rebuild and install the deb.  This is what I had to do.

---

### Post by docwhat on 2006-09-05
Quick Fix:

Cut and paste this into an sh shell.
--------->8--------cut---------8<----------
[ -f /bin/uname.real ] || mv /bin/uname /bin/uname.real ; touch uname; chmod +x uname ; cat >| uname <<EOF
#!/bin/bash
if [ "\$1" = "-r" ]; then
echo 2.6.20
else
exec uname.real "\$@"
fi
EOF
--------->8--------cut---------8<----------

When you're done, mv /bin/uname.real /bin/uname or reinstall coreutils.

What it does:
  If the -r flag is passed to uname, it returns 2.6.20, a version of the linux kernel that is higher than lvm2 is checking for.
  Otherwise, it runs the real uname.


Ciao!

---

### Post by ExemplarUbuntu on 2007-02-28
> **jeffvc said:**
> If anyone is still having this problem, this has been reported as a bug on Launchpad.  The solution to this problem is contained within the thread:

[https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972/](https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972/)

A summary follows:

The best solution is to put lvm2 on hold:

```
aptitude hold package_name
```



I have this problem and I am using the above method. It is taking a while setting-up, installing and de-installing lots of packages. Is this right ?

EDIT:
After an hour it crashed when setting up Gnome. Luckily it did re-boot (that was a novelty ;-)

I had to use dpkg to finish setting up Gnome and the dist-upgrade is now resumed.

Does the hold lvm2 have to be removed later ?

---


---
title: "Error installing slocate during Edgy upgrade"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by wammin on 2006-11-17
I'm upgrading from Dapper to Edgy using the Upgrade Manager as instructed. Everything seems to have worked except for this 'slocate' package which continues to fail. It's showing up as a broken package now in Synaptic, and it is a dependency of ubuntu-desktop so that is broken as well. When I try to fix the installation of slocate, this is what I get:

```

~$ sudo apt-get install slocate
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  slocate
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 30.2kB of archives.
After unpacking 156kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/main slocate 3.1-1 [30.2kB]
Fetched 30.2kB in 0s (31.2kB/s) 
(Reading database ... 107559 files and directories currently installed.)
Unpacking slocate (from .../slocate_3.1-1_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_3.1-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_3.1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is this serious? Any idea how to fix it?
Thanks

---

### Post by tim67 on 2006-11-26
Hi

I did "sudo rm find" in /etc/cron.daily,
and then re-installed ubuntu-desktop. now it 
doesn't show broken

-tim

---

### Post by xdarkxanarchyx on 2006-11-29
Yes, I was having problems too re-installing from a text/alternative i386 disc and this worked for me. :)

---

### Post by DarkEndymion on 2006-12-07
It also worked for me thanks.

By the way, do you remember how possibly it happened ?
I think it happened to me when I, by mistake, changed the owner of the files in /etc , from root to my personal user. I had to reinstall ubuntu, but not wanted to lose information, I didn't make a clean installation.

---


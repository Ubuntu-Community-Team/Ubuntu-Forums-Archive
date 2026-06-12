---
title: "New Updates, can't install"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by Tig3rzhark on 2008-02-28
I received a notice pertaining to updates for Ubuntu 7.10 amd64

these were the updates:

libnautilus-extension1

libvolume-id0

nautilus

nautilus-data

udev

volumeid

When I tried installing the updates, I received this error message:

E: /var/cache/apt/archives/libvolume-id0_113-0ubuntu17_amd64.deb: files list file for package `mono-runtime' is missing final newline

This is not the first time this has occured.  This has occured before with different packages.

Is there a solution to this error?  If so please tell me.

---

### Post by erginemr on 2008-02-29
There are two generic, omnipresent commands, which can be used to fix the dpkg installer database:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

On the other hand, if you receive the same error in the installation of different packages, but originating from volumeid, then there has to be something whong with the package "libvolume-id0".

---

### Post by Tig3rzhark on 2008-02-29
I've tried both commands.

So far it has failed to solve my problem.

I don't know what to do.

I can't install anything else until this problem is solved.

---

### Post by erginemr on 2008-02-29
One question about the error message "files list file for package 'mono-runtime' is missing final newline": Does the installer complain about 'mono-runtime' each time? I mean, do you remember if it has complained about mono-runtime in the past, too? 

AFAIK, mono is an attempt to incorporate .net technology to Linux, and another application on your system developed with mono may have needed it.

What happens if you try to uninstall mono-runtime with:
```
sudo aptitude remove mono-runtime
```

The installer will probably not obey this command, because some other application may need this one. Which program(s) needs this runtime library? 

I started to believe that there is something wrong in the lines in the dpkg database belonging to this package. FYI, the database is located here:

```
/var/lib/dpkg/status
```

Can you please take a copy of this file to your desktop via Nautilus, compress it to zip, tar.gz, etc. and attach it to your next post for us to check what is inside?

---

### Post by Tig3rzhark on 2008-02-29
I hope that this will help.

---

### Post by Pumalite on 2008-02-29
This is the first culprit:
Package: jfsutils
Status: purge ok not-installed
sudo dpkg --remove --force-remove-reinstreq jfsutils

---

### Post by erginemr on 2008-02-29
Unfortunately, your status file has revealed nothing except several "purge ok not-installed" remarks. I first thought Pumalite's suggestion will be the end of it all, but having checked my database file too, which has the same "not-installed" remark in at least two locations, I started to believe that this will not solve your problem.

```
E: /var/cache/apt/archives/libvolume-id0_113-0ubuntu17_amd64.deb: files list file for package `mono-runtime' is missing final newline
```

Can it be the case that the packages your installer has downloaded are corrupted? Hmm, worth a try...

Can you please run this command to cleanse your apt-get cache (i.e. downloaded Debian packages in the cache folder):
```
sudo aptitude clean
```
and open up "Main Menu -> Administration -> Software Sources" and select a different server than the one you have been using. Then fire up "Update Manager, press check and try to update your system again.

---


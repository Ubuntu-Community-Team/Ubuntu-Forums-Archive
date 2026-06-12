---
title: "apt-get upgrade failed"
date: 2014-12-18
forum: Installation &amp; Upgrades
---

### Post by antony9 on 2014-12-18
Hey guys Ive got a Zimbra mail server running on Ubuntu.

Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

I had a failed apt-get update && apt-get upgrade the other month and it didn't break or prevent anything from running but its an error I would like to solve if possible.

Below is the error I'm receiving:

root@zimbra:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.6) but 2.15-0ubuntu10.7 is installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10.6)
E: Unmet dependencies. Try using -f.
root@zimbra:~#


Obviously I have tried using -f but to no avail.

Could anyone throw some suggestions this way on how to eradicate this error?

Kind regards,
Antony.

---

### Post by Bashing-om on 2014-12-18
antony9; Hi ! Welcome to the forum .

What gets my attention:
> 
Depends: libc-dev-bin (= 2.15-0ubuntu10.6)

When what should be for this situation:
> 
You have searched for packages that names contain libc-dev-bin in suite(s) precise-updates, all sections, and all architectures. Found 1 matching packages.

Exact hits

Package libc-dev-bin

precise-updates (libdevel): Embedded GNU C Library: Development binaries 
2.15-0ubuntu10.9: amd64 i386

And as well:
You have searched for packages that names contain libc6 in suite(s) precise-updates, all sections, and all architectures. Found 12 matching packages.

Exact hits

Package libc6

precise-updates (libs): Embedded GNU C Library: Shared libraries 
2.15-0ubuntu10.9: amd64 i386 
also provided by: libc6-udeb


I propose that you have installed "development" (32 bit) package that is holding libc6 to a lower version.

Let's consider removing '  libc-dev-bin ' as per:
> 
sysop@1404mini:~$ apt-cache rdepends  libc-dev-bin
libc-dev-bin
Reverse Depends:
  libc-dev-bin:i386
  libc6-dev
    libc-dev-bin:i386
  libc-dev-bin:i386
  libc6-dev
sysop@1404mini:~$

I see nothing that the system at large depends on it;
What also results from terminal commands:
```

apt-mark showholds
apt-cache policy libc-dev-bin
apt-cache policy libc6

```

Maybe purging ' libc-dev-bin ' will give a way to proceed in a forward direction ?

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by antony9 on 2014-12-18
Thanks for you reply, I had previous tried purging and tried again with to no avail.

root@zimbra:~# apt-get purge --auto-remove libc-dev-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.6) but 2.15-0ubuntu10.7 is to be installed
             Depends: libc-dev-bin (= 2.15-0ubuntu10.6)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@zimbra:~#


This is a tricky one!

---

### Post by Bashing-om on 2014-12-18
antony9; OK ;

What results:
```

sudo apt-get purge libc6-dev 

```
??

[INDENT][INDENT][INDENT]maybe now 
[/INDENT][/INDENT][/INDENT]

---

### Post by antony9 on 2014-12-19
Thats done it! Thanks so much! :D

---

### Post by mörgæs on 2014-12-19
Good, please mark the thread 'solved'.

---


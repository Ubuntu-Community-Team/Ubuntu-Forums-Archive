---
title: "Help me read apt list upgradable output?"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by Monocerotis on 2020-04-24
I'm looking to update a Ubuntu 18.04 LTS installation. I mainly want a newer version of dnsutils.

Command:
```
sudo apt update
```

It told me:
```
221 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

Command:
```
apt list --upgradable
```

Filtered output:
```
dnsutils/bionic-updates,bionic-security 1:9.11.3+dfsg-1ubuntu1.11 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.3]
```

The name of the package is "dnsutils"?
What is "bionic-updates"?
What is "bionic-security"? I know "Bionic Beaver" is the codename of Ubuntu 18.04.
What does the "1:" in "1:9.11.3" mean?
What does "+dfsg" mean?
What is "-1ubuntu1.11"?
Is "9.11.3" the current version of dnsutils?
And "1ubuntu1.3" is the current version of... something?

---

### Post by deadflowr on 2020-04-24
bionic-update is the update repository, where all packages that have been updated for any given release come from.
bionic-security is the security repository where all security updates are.
the reaction between -updates and -security is like fingers and thumbs,
(all thumbs are fingers, but not all fingers are thumbs,
in that all security updates are -updates, but not all updates are -security.)
so since it's mainly a security update it is available in both the security repository and the updates repository.

On naming conventions see:
[https://www.debian.org/doc/debian-policy/ch-controlfields.html#version]("https://www.debian.org/doc/debian-policy/ch-controlfields.html#version")
[https://askubuntu.com/questions/11592/what-does-dsfg-as-a-part-of-package-names-mean]("https://askubuntu.com/questions/11592/what-does-dsfg-as-a-part-of-package-names-mean")

> Is "9.11.3" the current version of dnsutils?
And "1ubuntu1.3" is the current version of... something?

all strings are a single entity, so that is one package
9.11.3 would be the version installed but 1:9.11.3+dfsg-1ubuntu1.3 is the current package build you have installed from.

---

### Post by Monocerotis on 2020-04-24
bionic-update is the update repository, where all packages that have been updated for any given release come from.
bionic-security is the security repository where all security updates are.
the reaction between -updates and -security is like fingers and thumbs,
(all thumbs are fingers, but not all fingers are thumbs,
in that all security updates are -updates, but not all updates are -security.)
so since it's mainly a security update it is available in both the security repository and the updates repository.

On naming conventions see:
[https://www.debian.org/doc/debian-policy/ch-controlfields.html#version](https://www.debian.org/doc/debian-policy/ch-controlfields.html#version)
[https://askubuntu.com/questions/11592/what-does-dsfg-as-a-part-of-package-names-mean](https://askubuntu.com/questions/11592/what-does-dsfg-as-a-part-of-package-names-mean)



all strings are a single entity, so that is one package
9.11.3 would be the version installed but 1:9.11.3+dfsg-1ubuntu1.3 is the current package build you have installed from.[/QUOTE]

> **deadflowr said:**
> bionic-update is the update repository, where all packages that have been updated for any given release come from.
bionic-security is the security repository where all security updates are.

[LIST]
[*]bionic-update: Update repository for Bionic Beaver. 
[/LIST]
 
[LIST]
[*]bionic-security: Security update repository for Bionic Beaver. 
[/LIST]
 
> the reaction between -updates and -security is like fingers and thumbs,
(all thumbs are fingers, but not all fingers are thumbs,
in that all security updates are -updates, but not all updates are -security.)

So you're saying that bionic-update is a repository for updates, but not for security updates, and that bionic-security is a repository for security updates, but not for non-security updates?

> so since it's mainly a security update it is available in both the security repository and the updates repository.
Does that mean that there is a dependency between bionic-security and bionic-updates?

> all strings are a single entity, so that is one package
Are you saying the name of the package is "dnsutils/bionic-updates,bionic-security 1:9.11.3+dfsg-1ubuntu1.11 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.3]"?

Is "dnsutils" not the package name then?

Could it be that "dnsutils" is the name of the binary executable and that "1:9.11.3+dfsg-1ubuntu1.3" is the name of the source package it was built from? So then "upgradable from: 1:9.11.3+dfsg-1ubuntu1.3" would mean that "dnsutils" can be upgraded using the "1:9.11.3+dfsg-1ubuntu1.3" source package from the bionic-security and bionic-updates repositories?

> **Monocerotis said:**
> What does "+dfsg" mean?
I don't know about the plus sign, but dfsg stands for Debian Free Software Guidelines.

---

### Post by Monocerotis on 2020-04-24
Preparing to unpack .../2-dnsutils_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking dnsutils (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Setting up dnsutils (1:9.11.3+dfsg-1ubuntu1.11) ...

So this is what I had:
```
1:9.11.3+dfsg-1ubuntu1.11 amd64 [upgradable from: 1:9.11.3+dfsg-1ubuntu1.3]
```

If I run "apt show dnsutils" I get the following version number out.

```
 Package: dnsutils
Version: 1:9.11.3+dfsg-1ubuntu1.11
```

So I have successfully upgraded to version "1:9.11.3+dfsg-1ubuntu1.11"? From "1:9.11.3+dfsg-1ubuntu1.3"? So the first set of numbers did not change, but the second set did, "1ubuntu1.1" vs. "1ubuntu1.3"?

---

### Post by Monocerotis on 2020-04-24
> **Monocerotis said:**
> Could it be that "dnsutils" is the name of the binary executable and that "1:9.11.3+dfsg-1ubuntu1.3" is the name of the source package it was built from?
Seems reasonable.

> **Monocerotis said:**
> So then "upgradable from: 1:9.11.3+dfsg-1ubuntu1.3" would mean that "dnsutils" can be upgraded using the "1:9.11.3+dfsg-1ubuntu1.3" source package from the bionic-security and bionic-updates repositories?
I don't think so. The "from" refers not to the source package the new executable will be built from, but the source package the currently installed executable was built from. In other words, "1:9.11.3+dfsg-1ubuntu1.3" is what is currently installed, and "1:9.11.3+dfsg-1ubuntu1.11" is what will be installed if the "package" (executable) is upgraded.

Then it would also mean that "9.11.3" is not the version number. But the whole thing is, so "9.11.3+dfsg-1ubuntu1.3".

---

### Post by CatKiller on 2020-04-24
> **Monocerotis said:**
> The name of the package is "dnsutils"?
What is "bionic-updates"?
What is "bionic-security"? I know "Bionic Beaver" is the codename of Ubuntu 18.04.
What does the "1:" in "1:9.11.3" mean?
What does "+dfsg" mean?
What is "-1ubuntu1.11"?
Is "9.11.3" the current version of dnsutils?
And "1ubuntu1.3" is the current version of... something?

deadflowr has already covered the different repositories and their function. In this case, dnsutils is the name of the package. The version string doesn't have any inherent meaning. It increments, so that a newer version has a higher number, since otherwise it confuses everybody - *especially* the package manager. Apart from that, it could contain anything - whatever makes sense to the person that created the package. Different maintainers, and different projects, have their own habits for what information they might choose to include in the version string. The filename of the package itself could be called absolutely anything - it doesn't have to be related in any way to either the name or the version string - but people try to avoid having it completely arbitrary since that would just confuse everyone.

---

### Post by Monocerotis on 2020-04-24
> **CatKiller said:**
> deadflowr has already covered the different repositories and their function. In this case, dnsutils is the name of the package. The version string doesn't have any inherent meaning. It increments, so that a newer version has a higher number, since otherwise it confuses everybody - *especially* the package manager. Apart from that, it could contain anything - whatever makes sense to the person that created the package. Different maintainers, and different projects, have their own habits for what information they might choose to include in the version string. The filename of the package itself could be called absolutely anything - it doesn't have to be related in any way to either the name or the version string - but people try to avoid having it completely arbitrary since that would just confuse everyone.

OK, so "dnsutils" is the package name and "1:9.11.3+dfsg-1ubuntu1.11" is the version string then?

I  just realized that all the different lines had the same string attached  to them during the upgrade process. You can see that below.

```
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libirs160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [19.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 bind9-host amd64 1:9.11.3+dfsg-1ubuntu1.11 [53.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 dnsutils amd64 1:9.11.3+dfsg-1ubuntu1.11 [145 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libbind9-160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [27.6 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccfg160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [48.5 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccc160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [17.9 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libdns1100 amd64 1:9.11.3+dfsg-1ubuntu1.11 [966 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisc169 amd64 1:9.11.3+dfsg-1ubuntu1.11 [237 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblwres160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [34.5 kB]
Fetched 1549 kB in 2s (845 kB/s)
```

All of these are packages, right? And they all use the same version string for identification purpose? Is this because they all belong to the same parent package? Here is a complete log.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libfreetype6
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  bind9-host libbind9-160 libdns1100 libirs160 libisc169 libisccc160 libisccfg160 liblwres160
Suggested packages:
  rblcheck
The following packages will be upgraded:
  bind9-host dnsutils libbind9-160 libdns1100 libirs160 libisc169 libisccc160 libisccfg160 liblwres160
9 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.
Need to get 1549 kB of archives.
After this operation, 9216 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libirs160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [19.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 bind9-host amd64 1:9.11.3+dfsg-1ubuntu1.11 [53.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 dnsutils amd64 1:9.11.3+dfsg-1ubuntu1.11 [145 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libbind9-160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [27.6 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccfg160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [48.5 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisccc160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [17.9 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libdns1100 amd64 1:9.11.3+dfsg-1ubuntu1.11 [966 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisc169 amd64 1:9.11.3+dfsg-1ubuntu1.11 [237 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblwres160 amd64 1:9.11.3+dfsg-1ubuntu1.11 [34.5 kB]
Fetched 1549 kB in 2s (845 kB/s)
(Reading database ... 29459 files and directories currently installed.)
Preparing to unpack .../0-libirs160_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libirs160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../1-bind9-host_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking bind9-host (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../2-dnsutils_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking dnsutils (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../3-libbind9-160_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libbind9-160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../4-libisccfg160_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libisccfg160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../5-libisccc160_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libisccc160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../6-libdns1100_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libdns1100:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../7-libisc169_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking libisc169:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Preparing to unpack .../8-liblwres160_1%3a9.11.3+dfsg-1ubuntu1.11_amd64.deb ...
Unpacking liblwres160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) over (1:9.11.3+dfsg-1ubuntu1.3) ...
Setting up libisc169:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up libisccc160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up libdns1100:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up liblwres160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up libisccfg160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up libirs160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up libbind9-160:amd64 (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up bind9-host (1:9.11.3+dfsg-1ubuntu1.11) ...
Setting up dnsutils (1:9.11.3+dfsg-1ubuntu1.11) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
```

I did a search for dnsutils and found this page:
[https://launchpad.net/ubuntu/+source/bind9](https://launchpad.net/ubuntu/+source/bind9)

How is dnsutils related to bind9? Are they one and the same? It seems to me like the "1:9.11.3+dfsg-1ubuntu1.11" version string belongs to bind9 package as a whole, and to all the different packages that are contained within it, including dnsutils?

Also note how it says on that page: "dnsutils: Transitional package for bind9-dnsutils". Does that mean that "dnsutils" is just an alias for "bind9-dnsutils"? And then when I go upgrade "dnsutils" it really upgrades "bind9-dnsutils" which pulls in everything else that it depends on that is included in the "bind9" package as a whole? Or is "dnsutils" completely separate from "bind9-dnsutils" and should not be confused? I don't see it listed... I could only find that page. Does dnsutils have its own page somewhere else?

I may be jumping the gun here, and I'm sorry if this has been covered already elsewhere on the www. I just want to understand a bit better what these commands are telling me, and also understand the system better. I am one of those eternal noobs when it comes to GNU/Linux, but not a complete computer noob.

---

### Post by CatKiller on 2020-04-24
Yes, related packages will often have the same version string - the Plasma packages, for example, or the Nvidia driver packages. Yes, sometimes package names change, and a package with the old name will depend on the package with the new name, so that people that are using the old name will get the new package. Those are definitely both things that happen. I haven't looked into the specifics of the packages that you're interested in.

---

### Post by Monocerotis on 2020-04-25
> **CatKiller said:**
> Yes, related packages will often have the same version string - the Plasma packages, for example, or the Nvidia driver packages. Yes, sometimes package names change, and a package with the old name will depend on the package with the new name, so that people that are using the old name will get the new package. Those are definitely both things that happen. I haven't looked into the specifics of the packages that you're interested in.

Sounds reasonable. So what happens to the old package with the old name? Is it eventually removed in the upcoming major release of Ubuntu for example? So that only the new name is used going forward?

---

### Post by CatKiller on 2020-04-25
> **Monocerotis said:**
> Sounds reasonable. So what happens to the old package with the old name? Is it eventually removed in the upcoming major release of Ubuntu for example? So that only the new name is used going forward?

Yes, eventually. A package that contains no data but just depends on another package takes up essentially no space - for the user, or on the repository server - so there's no rush. The main thing is to get users onto the new package.

---

### Post by Monocerotis on 2020-04-26
I have one more question regarding versions and "upstream" vs. "downstream" packages.

On this page:
[https://launchpad.net/ubuntu/+source/bind9](https://launchpad.net/ubuntu/+source/bind9)

I clicked on the "show upstream links" link which brought me here:
[https://launchpad.net/bind/+packages](https://launchpad.net/bind/+packages)

This is a page where the "BIND" people display different versions of the bind9 package before it is integrated (downstream) with Ubuntu?

I can see these two versions:
1:9.11.3+dfsg-1ubuntu1.11
1:9.11.4+dfsg-3ubuntu5.4

I have both of these on two different computers, one is Bionic (18.04), the other is Cosmic (18.10). (I know it's no longer supported, I don't use the 18.10 computer at the moment.)

But I cannot see this version that I upgraded from previously:
1:9.11.3+dfsg-1ubuntu1.3

Why is it not listed?

---


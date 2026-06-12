---
title: "apt-get problems"
date: 2021-02-04
forum: Installation &amp; Upgrades
---

### Post by c_schmitz on 2021-02-04
Hello,

I am still using  Ubuntu Xenial 16.04.07 LTS (yes, I will upgrade soon)
I have installed munin apt-all module to check on pending packaged and it reports to me that there are several packages to be updated.
When I do (as root)

```

> apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sooo...no packages to update.
However when I do

```
> apt-get upgrade -t xenial
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  debhelper
The following packages will be upgraded:
  libarchive13
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 283 kB of archives.
After this operation, 59.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
```

I get the above. 
Can someone explain to me (like I am five) what is the difference here?  Why does the 1st command does not show anything to upgrade, but the  second one does?
To be honest I don't understand the "-t xenial" option, even after reading the apt-get manual.

Thank you in advance.

Best regards

Chris

---

### Post by TheFu on 2021-02-05
I don't know. Let's do a little research:

```
$ dpkg -l libarchive13*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libarchive13:a 3.2.2-3.1ubu amd64        Multi-format archive and compress
```

That is a meta-package ... used to get other real, packages, those that have actual binary code. Let's get the package to tell us something, 
```
$ dpkg -f /var/cache/apt/archives/libarchive13_3.2.2-3.1ubuntu0.6_amd64.deb
...
Depends: libacl1 (>= 2.2.51-8), libbz2-1.0, libc6 (>= 2.16), liblz4-1 (>= 0.0~r130), liblzma5 (>= 5.2.2), liblzo2-2, libnettle6, libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4)
Suggests: lrzip
Section: libs
Priority: **optional**
Multi-Arch: **same**
```

The dependencies are "fuzzy". See the "multi-arch" part?  That means this "package" doesn't have any CPU specific code, which is expected for meta-packages.

That's what I see.

The apt-get manpage says -t pins the package, which probably isn't what you want.
```
       -t, --target-release, --default-release
           This option controls the default input to the policy
           engine; it creates a default **pin** at priority 990 using
           the specified release string. This overrides the general
           settings in /etc/apt/preferences. Specifically pinned
           packages are not affected by the value of this option.
           In short, this option lets you have simple control over
           which distribution packages will be retrieved from. Some
           common examples might be -t '2.1*', -t unstable or -t
           sid. Configuration Item: APT::Default-Release; see also
           the apt_preferences(5) manual page.
```

---


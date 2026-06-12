---
title: "Error When Upgrading libimobiledevice1"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by hayhursm on 2011-04-06
Hello everyone,

I cannot seem to find a solution to this problem but when performing a: **sudo apt-get upgrade** I get the following error for **libimobiledevice1**:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libimobiledevice1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.2kB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/) lucid/main libimobiledevice1 1.0.6-1ubuntu1~lucid1 [48.2kB]
Fetched 48.2kB in 0s (63.7kB/s)          
(Reading database ... 187251 files and directories currently installed.)
Preparing to replace libimobiledevice1 1.0.4-1ubuntu1~lucid1 (using .../libimobiledevice1_1.0.6-1ubuntu1~lucid1_amd64.deb) ...
Unpacking replacement libimobiledevice1 ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0:0.9.7-1ubuntu1
Processing triggers for hal ...
Regenerating hal fdi cache ...
Errors were encountered while processing:
 /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

I've never encountered this type of error when performing a daily upgrade and I cannot find a solution anywhere on the net.  Any help is always appreciated!

---

### Post by bashologist on 2011-04-06
Same problem here from using ppa:pmcenery/ppa. Hopefully a fix soon. Would an update fix it or is there a permanent problem I wonder??


> [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

libimobiledevice 32 hours ago
Successfully built

---

### Post by Barbalras on 2011-04-14
same problem here!

---

### Post by hayhursm on 2011-04-14
> **Barbalras said:**
> same problem here!

Are you using the [https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa") ppa?

---

### Post by Mr. Beekeeper on 2011-04-16
I might have found a solution, I don't know for sure.  I went into System>Administration>Synaptic Package Manager.  In Synaptic, I went to Settings>Repositories.  Under "Other Software" I checked both "Canonical Partners" and "Canonical Partners (Source Code)".  Clicked close and ran Update Manager.  I don't have problems with it anymore.  If you look at the package in Synaptic, It says that it's version 1.0.4.  It also says that's the current version.  I don't know, but it seems to have fixed the annoying "Package failed to install" problem.  Extra points if I solved a problem on the first post?

:cool:

---

### Post by wollac on 2011-04-16
I have the same issue also. Tried what Mr. Beekeeper suggested but I already had Canonical Partners checked and Canonical Partners (source) was not there as an option.

Anyone had any luck getting it to work or found any news related to this issue?

---

### Post by Barbalras on 2011-04-17
> **hayhursm said:**
> Are you using the [https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/%7Epmcenery/+archive/ppa") ppa?

Yes I am

Cheers!

---

### Post by SLeeePLESS on 2011-10-02
I just removed "libimobiledevice0 0:0.9.7-1ubuntu1" in synaptic then updated libimobiledevice1 and it seemed to work fine.

I'm not sure if this is still and issue, but I was getting a similar error message when I updated from lucid to maverick. Hope this helped.

---


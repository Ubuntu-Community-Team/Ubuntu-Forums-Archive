---
title: "Update Manager Problems and Unmet Dependencies"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by mission_difficult on 2009-12-18
A few weeks ago I received a message from the update manager reading
  ```

Could not calculate the upgrade.

A unresolvable problem occurred while calculating the upgrade. Please report this bug
against the 'update-manager' package and include the following error message:
'E:Error,pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

```When I run apt-get dist-upgrade I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
  gconf2-common: Depends: ucf but it is not going to be installed
  libfontconfig1: Depends: fontconfig-config (= 2.5.0-2ubuntu3) but it is not going to be installed
  libpam-modules: Depends: libpam0g (>= 0.99.7.1) but it is not going to be installed
  libsasl2-2: Depends: libsasl2-modules (= 2.1.22.dfsg1-18ubuntu2.1) but it is not going to be installed or
                       libsasl2-modules-sql (= 2.1.22.dfsg1-18ubuntu2.1) but it is not going to be installed or
                       libsasl2-modules-gssapi-heimdal (= 2.1.22.dfsg1-18ubuntu2.1) but it is not going to be installed or
                       libsasl2-modules-kerberos-heimdal (= 2.1.22.dfsg1-18ubuntu2.1) but it is not installable
  python2.5: Depends: libssl0.9.8 (>= 0.9.8f-1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```I'm running Ubuntu 8.04. Thanks in advance!

---

### Post by tommcd on 2009-12-18
To attempt a quick fix, open synaptic package manager (system > administration > synaptic package manager). Then select Edit > Fix Broken Packages.
This *may* fix the problem. This was reported on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/365875](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/365875)
The only attempt at a fix was to run:
```
sudo apt-get install -f
```
Try that if synaptic can't fix the problem. If I find a more definitive fix, I will post it here.
Question: Are you only using the official Ubuntu repositories for 8.04? Or have you added other unofficial repositories, like the ppa repos or other repos, to your sources.list?

And welcome to the Ubuntu forums!

---

### Post by mission_difficult on 2009-12-18
I've checked in Synaptic and haven't seen any broken packages.
When I try apt-get install -f I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```I should have mentioned that I am using the eeepc kernel (linux-image-2.6.24-21-eeepc) from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)

My sources.list contains the following uncommented items:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ hardy main
```

---

### Post by kansasnoob on 2009-12-18
I would be tempted to run:

```
sudo apt-get clean
```

which will remove .deb files even for packages currently installed. Most of the time you probably don't need the .debs anyway, but you may find at some point you'll need to DL some previously installed .deb.

Then of course run:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tommcd on 2009-12-19
> **mission_difficult said:**
> I should have mentioned that I am using the eeepc kernel (linux-image-2.6.24-21-eeepc) from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)

My sources.list contains the following uncommented items:
```

deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ hardy main
```
I knew it. This is the risk that you take when you introduce unofficial repositories into the mix. The quality of unofficial repos varies widely.
I would try commenting out all those unofficial repos and try to run:
```

sudo apt-get update
sudo apt-get dist-upgrade.

```
If that fixes it, you can try adding back the unofficial repos one at a time to see if you can find the one that is causing the problem. I would bet that wine repository would be the one that has gone rogue on you. So add that one back last.

---

### Post by mission_difficult on 2009-12-22
Turns out it was the XBMC repositories. I was able to add everything else back without any  issues. So do I'm guessing that I just keep that off my list? Thanks for your help so far. It's a relief to have my panel clear of that failed upgrade icon. :P

---

### Post by tommcd on 2009-12-22
> **mission_difficult said:**
> Turns out it was the XBMC repositories. I was able to add everything else back without any  issues. So do I'm guessing that I just keep that off my list? Thanks for your help so far. It's a relief to have my panel clear of that failed upgrade icon. :P
You could try asking the XBMC team at Launchpad, or read through their mailing lists:
[https://launchpad.net/~team-xbmc](https://launchpad.net/~team-xbmc)
If synaptic or "apt-get install -f" could not fix the dependencies then I don't know what else you could do.

---


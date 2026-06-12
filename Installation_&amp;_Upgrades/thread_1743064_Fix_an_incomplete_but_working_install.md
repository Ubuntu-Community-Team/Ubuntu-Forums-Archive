---
title: "Fix an incomplete but working install?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by lupusnoctu on 2011-04-29
Hello. I recently got a new machine with more updated hardware than the old one I had running my network server. When I installed Ubuntu 10.10 Server to it, Everything went fine up until it started configuring apt and pulling in some of the base packages, at which point, it said something about tasksel and then quickly switched to a red error screen. I no longer recall what the error said, but I tried that part of the install process 3 times with no luck. I figured I could fix it later once I got it up and running, so I bypassed that step. It was the same step where the installer asks you what kind of servers to pull in such as LAMP, openssh, mail, etc. 

The machine is up and running, and pretty well, but some of the basic packages are missing, such as mlocate. I've installed the ones that have gotten in my way and all my desired servers, but I'm wondering if there's a metapackage or some other fix that I can do to essentially do what the installer should have? Or am I going to keep installing these packages as I need them and find they're missing? I've already manually configured apt to use some internet mirrors, but I'm not sure that's sufficient. I haven't seen any upgrades come down the line since installation. Below is my sources.list

```

mark@hermes:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu maverick main restricted
deb http://us.archive.ubuntu.com/ubuntu maverick-updates universe multiverse

```

On a side note, when I try to install SWAT (Samba Web Administration Tool), I'm told:

```

mark@hermes:~$ sudo apt-get install swat
[sudo] password for mark:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 swat : Depends: samba (= 2:3.5.4~dfsg-1ubuntu8.4) but 2:3.5.4~dfsg-1ubuntu8 is to be installed
        Recommends: samba-doc (= 2:3.5.4~dfsg-1ubuntu8.4) but 2:3.5.4~dfsg-1ubuntu8 is to be installed
E: Broken packages

```
Yet, I do have samba and samba-doc installed. I have tried apt-get -f install to no avail. I'm stuck, as I've never had issues with apt before.

Help on any or all of these is greatly appreciated. Thank you.

---


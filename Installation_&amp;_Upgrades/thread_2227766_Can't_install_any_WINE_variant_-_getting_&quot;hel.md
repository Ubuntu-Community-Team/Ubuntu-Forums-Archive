---
title: "Can't install any WINE variant - getting &quot;held broken packages&quot; error messag"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by stealthdave on 2014-06-03
I'm trying to re-install pipelight after upgrading to 14.04 from a working 13.10 Xubuntu installation on the amd64 architecture.  I've successfully added the repository, but when I try to install, I get the following error message:

```
$ sudo apt-get install pipelightReading package lists... DoneBuilding dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 pipelight : Depends: pipelight-multi but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Forcing install has no effect:

```
$ sudo apt-get install -fReading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

The results of **sudo apt-mark showhold** shows no packages have been "held".  I have purged pipelight, pipelight-multi, wine-compholio and wine-conpholio-i386, but still no success.  Synaptic GUI shows ***NO BROKEN PACKAGES!!!***

I also discovered that I could not install *any* version of wine, so I tried adding the i386 architecture manually with the following command:

```
$ sudo dpkg --add-architecture i386
```

Same issue results.  I suspect that this is an issue with installing *any* i386 architecture software.  This is my media PC that I use for Netflix, HBO Go, etc, so Pipelight is pretty vital to its core function.  Any help would be greatly appreciated!

---

### Post by stealthdave on 2014-06-04
Well, that was an obnoxious problem!  It looks like there's an issue with some of the repository mirrors.  I used Synaptic to change the repository mirror from **us.archive.ubuntu.org** to **mirrors.us.kernel.org**, and all of the i386 architecture packages magically became available.

---


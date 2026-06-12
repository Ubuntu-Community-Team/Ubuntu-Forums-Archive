---
title: "libc6 dependency issues preventing any installations"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by bfcrowrench on 2012-12-29
Hi All!

I'm running a Wubi install of Kubuntu 12.04, 64-bit.  

I'm experiencing a problem in apt-get when I try to do any install or upgrade.  It complains of a dependency issue which I have not been able to resolve on my own.  

Here's the output of apt-get when I attempt to resolve:

```
raoulduke@ubuntu ~> sudo apt-get -f install
[sudo] password for raoulduke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-26-generic libkipi8 libdiscid0 libkwinactiveeffects1abi3 linux-headers-3.2.0-24 linux-headers-3.2.0-26 linux-headers-3.2.0-29 libglew1.5
  linux-headers-3.2.0-29-generic libkwineffects1abi3 linux-headers-3.2.0-24-generic libnepomukdatamanagement4 kdegraphics-mobipocket libkexiv2-10 libmusicbrainz3-6
  libkwinactiveglutils1 libkwinglutils1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libc6-i386
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6-dev libc6-i386
2 upgraded, 0 newly installed, 0 to remove and 230 not upgraded.
2 not fully installed or removed.
Need to get 0 B/6,938 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
 libc6-dev depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 libc6-dev
 libc6-i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've been trying without success to downgrade my libc6 package; not ideal perhaps a necessary evil if it will let me proceed with upgrades to my system.

I posted earlier to an [existing thread that seemed to be on the same issue]("http://ubuntuforums.org/showthread.php?t=2075635"), but then I noticed a small discrepancy in the errors and thought I had better start a new thread.

Any suggestions are appreciated!   Thanks!

---

### Post by bfcrowrench on 2012-12-29
I just tried a *dist-upgrade* and I'm getting the following error:

```
raoulduke@ubuntu ~> sudo apt-get dist-upgrade 
[sudo] password for raoulduke:                                                                                                                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)                                                                                      
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?           
```

I'm still stumped.  Ideas welcome!

---

### Post by bfcrowrench on 2012-12-29
This may be a little premature, but I decided to try a GUI approach instead of apt-get and I seem to be having some luck.

[This guide]("https://help.ubuntu.com/community/QuantalUpgrades/Kubuntu") was helpful and may contain the solution:  it guided me to adjusting settings that allowed me to use a normal release cycle instead of the LTS cycle.

The upgrade is downloading, but if it's successful I'll confirm and close this.

---

### Post by bfcrowrench on 2012-12-30
Hi,

The dist upgrade from the GUI (Muon) was a success.   I expect the critical part was selecting a normal release cycle as described in the instructions (link in previous message).

I would call this solved -- but I don't know how to :)   I can't seem to find the option to change the prefix on the title from [kubuntu] to [solved].

If that's a mod operation, then you can go ahead and close this.

Thanks!!

~b

---


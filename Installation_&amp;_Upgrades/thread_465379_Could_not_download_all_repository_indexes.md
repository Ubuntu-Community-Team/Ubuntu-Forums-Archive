---
title: "Could not download all repository indexes"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by janb on 2007-06-05
I 've got a problem similar to other postings, but I can't seem to get to the bottom of this.

What is different in my case is the error code at the back:

> [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 502 Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )

I'm confused by this 502 proxy error.
How do I tell the update manager, package manager, etc... to use the proxy I also needed to configure for Firefox?
Yep, that one needed a proxy to make it work. Firefox DOES work like a train though. But anything synaptic, and it bombs out.

Just in case, here is the full story:

trying to update or install from an ubuntu approved repository, it tries to access package information. When trying to download the applicable package information, it keeps on running saying it 
> Failed, 0 bytes loaded
This continues for several files

Then eventually, it comes up with 
> [SIZE="6"]Could not download all repository indexes[/SIZE]

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
and in the window below listing all the addresses with the '502 Proxy error' as in above.

This is from a fresh installation of feisty.
I actually installed it before, giving the same problems, but I thought I buggered around to much and just decided to re-install the whole system.
I tried different servers in the Software Sources, but to no avail.

In case you're wondering, this is my source list:

> deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted

deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted



## Major bug fix updates produced after the final release of the

## distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe

deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse

deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


I also pinged the above sites, and that seems to work:

> PING ubuntu-archive.mirror.ac.za (155.232.137.129) 56(84) bytes of data.

64 bytes from 155.232.137.129: icmp_seq=1 ttl=240 time=710 ms

64 bytes from ubuntu-archive.mirror.ac.za (155.232.137.129): icmp_seq=2 ttl=240 time=710 ms



PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.

64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=1 ttl=47 time=567 ms


Is this indeed a problem with the proxy, and if yes, how do I fix this?
Any ideas anyone?
Thanks,
Jan.

---

### Post by janb on 2007-06-05
Oh I found it.
System -> Preferences -> Network Proxy.
Now it works.
Silly me....

---

### Post by SIobber on 2007-12-14
Jan, I've been encountering similar errors... What did you to to your System>Preferences>Network Proxy ?

---

### Post by Partyboi2 on 2007-12-14
> **SIobber said:**
> Jan, I've been encountering similar errors... What did you to to your System>Preferences>Network Proxy ?
If you are needing to use proxy settings for apt.
Open up Synaptic Package Manager (System>Admin>Synaptic Package Manager.)
Click on Settings>Preferences>Network tab

---


---
title: "Can't install VLC player ?!"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by 828688 Ben on 2010-07-24
Here is the terminal output:

> ben@ben-desktop:~$ sudo apt-get install vlc mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
                      Depends: libvlc2 (>= 1.0.0~rc1) but it is not going to be installed
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.1) but it is not going to be installed
       Depends: libvlccore2 (>= 1.0.0~rc1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1.1) but it is not going to be installed
E: Broken packages
ben@ben-desktop:~$ 


What's happening?


Thanks,
Ben

---

### Post by dineshs on 2010-07-24
Did you try via synaptic package manager?

---

### Post by 828688 Ben on 2010-07-24
I tried that, but here's what happens when I try to install that way:
[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TEso4b_8bfI/AAAAAAAAAV4/-uy8NtCEP1M/Screenshot.png[/IMG]


Thanks,
Ben

---

### Post by 828688 Ben on 2010-07-24
I fixed it!
I unchecked > [http://ppa.launchpad.net/motumedia/ppa/ubuntu](http://ppa.launchpad.net/motumedia/ppa/ubuntu) from my software sources and it worked perfectly.

Thanks anyways,
Ben

---

### Post by dineshs on 2010-07-24
Did you do this?
system administration-synaptic package manager-settings-repositories
select main, universe, multiverse ,restricted -close then reload

---

### Post by Jazzy_Jeff on 2010-07-24
Please make this as solved as long as every thing is working now.

---

### Post by mcbelisle on 2010-08-04
I've been having problems installing vlc player also. I just reinstalled ubuntu 10.10 alpha and did not have any ppa's on the system and my vlc cannot install at all.

---

### Post by reddy.shyam on 2010-08-04
> **mcbelisle said:**
> I've been having problems installing vlc player also. I just reinstalled ubuntu 10.10 alpha and did not have any ppa's on the system and my vlc cannot install at all.


Same here. Some help would be appreciated.

> $ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 1.1.1-1+exp1ubuntu1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.1-1+exp1ubuntu1) but it is not going to be installed
E: Broken packages

---

### Post by reddy.shyam on 2010-08-05
Looks like official repository is fixed. The above command works now.

---


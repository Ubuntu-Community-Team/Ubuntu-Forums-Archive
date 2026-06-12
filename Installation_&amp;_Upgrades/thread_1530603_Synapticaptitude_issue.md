---
title: "Synaptic/aptitude issue"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by s6long1 on 2010-07-13
Hi all,

I am having update issues with my fiancé's laptop. It is a Dell Inspiron 1521, AMD64 (with Lucid 64 bit). It seems like I have a dependency problem somewhere, but I don't know how to fix it. When in Aptitude (Synaptic wont work), I've tried to find broken packages, and none are found, and "sudo aptitude -f" doesnt work either. Any ideas? 


> 
sudo aptitude update
...
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_deluge-team_ppa_ubuntu_dists_lucid_main_binary-amd64_Packages)
E: Problem parsing dependency Depends
E: Error occurred while processing gnome-codec-install (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Problem parsing dependency Depends
E: Error occurred while processing gnome-codec-install (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

E: Problem parsing dependency Depends
E: Error occurred while processing gnome-codec-install (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by snowpine on 2010-07-13
Your fiancé messed up his/her system by adding some junk to the software sources. I'd recommend System->Administration->Software Sources (or 'gksu gedit /etc/apt/sources.list') and trimming it down to the official Ubuntu software sources.

---

### Post by s6long1 on 2010-07-14
Did that, but still having the same problem. Also tried:
> sudo dpkg-reconfigure -a
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 21645 package 'gnome-codec-install':
 `Depends' field, syntax error after reference to package `gnome-icon-themer'
/usr/sbin/dpkg-reconfigure: acpi-support is not installed
No help there either. Confusing too, because according to [this link]("http://packages.ubuntu.com/lucid/gnome-codec-install") gnome-codec-install does not depend on acpi-support. Odd, and since gdebi doesn't work either, I am at a loss on how I'm supposed to install anything now...
Help!

---

### Post by s6long1 on 2010-07-18
BUMP!

Am I really going to have to do an Ubuntu re-install?

---

### Post by s6long1 on 2010-07-19
Boom! Got it working:
> sudo dpkg --configure -a
This gave me the exact location of the problem: a malformed line in /var/lib/dpkg/status that was giving me the problems. Not known how that error occurred, but all fixed now!

---


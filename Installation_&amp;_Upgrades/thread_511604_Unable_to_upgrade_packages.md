---
title: "Unable to upgrade packages"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by thebasard on 2007-07-28
I am getting the following error for any of the 20 package updates that need to be applied.  Running 7.04.

cdillard@jetfighter:~$ sudo apt-get clean
cdillard@jetfighter:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  app-install-data-commercial apport bind9 bind9-host dnsutils gnochm
  gnome-app-install iptables language-pack-en language-pack-gnome-en lftp
  libbind9-0 libdns22 libisc11 libisccc0 libisccfg1 liblwres9
  libnetaddr-ip-perl tzdata unattended-upgrades
20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: The package index files are corrupted. No Filename: field for package tzdata.

What should I do to resolve this?

---

### Post by thebasard on 2007-08-02
Also getting this error:

sudo apt-get clean && sudo apt-get check
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by thebasard on 2007-08-03
This sux!

Anybody got any ideas on how to fix this?

I've tried deleting the lock files in all apt/cache related directories I could find.

thanks,
ctd

---

### Post by forestpixie on 2007-08-04
I've found this in launchpad which might help you out - 

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/105179](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/105179)

have a look at the last 2 posts and see if that works if not post back

Edit - included in todays updates for me was a new version of tzdata!

---


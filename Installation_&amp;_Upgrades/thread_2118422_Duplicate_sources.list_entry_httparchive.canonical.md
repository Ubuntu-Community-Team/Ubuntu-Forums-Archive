---
title: "Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i38"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2013-02-21
Hi all
 since upgrading to 11.10 i am having issues whenever i do an apt-get update.
I keep on receiving this error
```

W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://uk.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

```

i tried to remove URL from sources.list in the hope that keep it to the bare minimum will fix the proble. and here's myc urrent sources.list
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse

###### Ubuntu Update Repos
# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse

###### Ubuntu Partner Repo
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

###### Ubuntu Extras Repo
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

But i still keep on getting the same problem, so i m wondering if the problem is actually in sources.list

could anyone assist?

w/kindest regards
 marco

---

### Post by mmistroni on 2013-02-21
Hi all
  looks like i have sorted all the erros below by following advices in
this thread

[http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)


sorry for the noise

w/kindest regards
 marco

---


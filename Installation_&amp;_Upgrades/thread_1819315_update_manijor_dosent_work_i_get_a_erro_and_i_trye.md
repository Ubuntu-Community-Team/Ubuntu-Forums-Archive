---
title: "update manijor dosent work i get a erro and i tryed evry code and they dont work"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by tony.mcvean on 2011-08-05
this is the erro i get 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by oldfred on 2011-08-06
Welcome to the forums.

Same error in this thread. Not sure if solution works or not:

[http://ubuntuforums.org/showthread.php?t=1819205](http://ubuntuforums.org/showthread.php?t=1819205)

---

### Post by tony.mcvean on 2011-08-06
nope that didnt work :(

---

### Post by tony.mcvean on 2011-08-06
no that didnt work

---

### Post by oldfred on 2011-08-06
Other than the link above I have not seen your specific problem. 

Can you boot?

If so I might try running the standard updates. You may want to check if some line in /etc/apt/sources.list is in error.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Also have you tried changing tothe best download source? 

System, Administration, Synaptic, settings, Repositories, download from combo box, other, Select best server.

---


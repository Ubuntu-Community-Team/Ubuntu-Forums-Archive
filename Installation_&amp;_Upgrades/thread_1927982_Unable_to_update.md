---
title: "Unable to update"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by Peacewise on 2012-02-19
When i run sudo apt-get update in ubuntu 11.10 i386 my terminal says:
 ```
   E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index (1) 
``` 
Please help me out

---

### Post by ajgreeny on 2012-02-19
Remove the files that are in /var/lib/apt/lists/partial/ after looking to see what is there.
```
ls -l /var/lib/apt/lists/partial/
``` it will probably list the faulty list that the error message reports so remove that with ```
sudo rm /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index (1)
```then update again with ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Peacewise on 2012-02-19
after doing sudo apt-get update i got an error message :
```
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index (1)

```
Although i had removed the file with the help of the above mentioned code.

---

### Post by Peacewise on 2012-02-19
This is the complete code that i get when i enter 
```
ls -l /var/lib/apt/lists/partial/
```

```
total 32748
-rw-r--r-- 1 root root      72 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root   12505 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    1645 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index
-rw-r--r-- 1 root root      14 2012-02-09 11:48 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources
-rw-r--r-- 1 root root       0 2012-02-09 11:48 archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root   10828 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   35254 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   80217 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_i18n_Index
-rw-r--r-- 1 root root      70 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root   12505 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root   29336 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages
-rw-r--r-- 1 root root  120364 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_i18n_Index
-rw-r--r-- 1 root root      72 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources.decomp
-rw-r--r-- 1 root root  134985 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   28615 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_i18n_Index
-rw-r--r-- 1 root root       0 2012-02-19 18:08 archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources.decomp
-rw-r--r-- 1 root root       0 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    2640 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root       0 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    3662 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index
-rw-r--r-- 1 root root  579052 2011-10-12 23:44 archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root   43194 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root  163420 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2263 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root       0 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root  596165 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2968 2012-02-18 03:45 archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index
-rw-r--r-- 1 root root    3289 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources.decomp
-rw-r--r-- 1 root root    9677 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root       0 2012-02-19 18:08 archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root  179981 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index
-rw-r--r-- 1 root root    3355 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources
-rw-r--r-- 1 root root   12505 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 1582667 2011-10-12 23:43 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 18:11 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages.decomp
-rw-r--r-- 1 root root  363921 2011-10-04 14:46 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root  179981 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index
-rw-r--r-- 1 root root       0 2012-02-19 18:07 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root    1491 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    5267 2011-10-12 23:47 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages.decomp
-rw-r--r-- 1 root root     369 2011-11-03 21:59 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    1172 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index
-rw-r--r-- 1 root root      73 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources.decomp
-rw-r--r-- 1 root root  861430 2011-10-12 11:02 archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 5792409 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 18:11 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    1827 2011-09-27 14:47 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   92569 2011-10-04 14:46 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index
-rw-r--r-- 1 root root      72 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources.decomp
-rw-r--r-- 1 root root   69756 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    1337 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages
-rw-r--r-- 1 root root    3179 2012-02-18 03:50 archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   96407 2012-02-18 03:45 archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index
-rw-r--r-- 1 root root    2265 2011-10-12 23:49 archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources.decomp
-rw-r--r-- 1 root root       0 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root       0 2012-02-19 17:20 archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    1491 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index
-rw-r--r-- 1 root root   25801 2012-02-18 03:45 archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    6563 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   19531 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2819 2012-02-09 11:48 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index
-rw-r--r-- 1 root root      71 2012-02-18 03:51 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root    1491 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    2207 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root    5172 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:48 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index
-rw-r--r-- 1 root root      74 2012-02-18 03:51 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 18:10 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources.decomp
-rw-r--r-- 1 root root       0 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-09 11:55 archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    7643 2012-02-09 11:48 archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index
-rw-r--r-- 1 root root       0 2012-02-19 18:08 archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources.decomp
-rw-r--r-- 1 root root   11381 2012-02-18 03:34 archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      72 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root 1582667 2011-10-12 23:43 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index
-rw-r--r-- 1 root root      14 2012-02-09 11:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources
-rw-r--r-- 1 root root       0 2012-02-09 11:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    1172 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:49 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    3549 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_i18n_Index
-rw-r--r-- 1 root root      70 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root 5792409 2011-10-12 23:49 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:49 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages.decomp
-rw-r--r-- 1 root root   50720 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_i18n_Index
-rw-r--r-- 1 root root      72 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources.decomp
-rw-r--r-- 1 root root  179981 2011-10-12 23:49 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:49 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages.decomp
-rw-r--r-- 1 root root  375837 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_i18n_Index
-rw-r--r-- 1 root root      70 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources.decomp
-rw-r--r-- 1 root root    2640 2011-10-12 23:49 in.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    3662 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index
-rw-r--r-- 1 root root   43194 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root  163420 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root  288223 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index
-rw-r--r-- 1 root root    2263 2011-10-12 23:49 in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root  123294 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages
-rw-r--r-- 1 root root  596165 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   96407 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index
-rw-r--r-- 1 root root    1337 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages
-rw-r--r-- 1 root root    3179 2012-02-18 03:50 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2968 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index
-rw-r--r-- 1 root root    2265 2011-10-12 23:49 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources.decomp
-rw-r--r-- 1 root root   18182 2011-10-12 23:47 in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      73 2012-02-18 03:51 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root      14 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index
-rw-r--r-- 1 root root    6355 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources
-rw-r--r-- 1 root root   25801 2012-02-18 03:45 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    6563 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   19531 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2819 2012-02-09 11:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index
-rw-r--r-- 1 root root      71 2012-02-18 03:51 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources.decomp
-rw-r--r-- 1 root root    2207 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root    5172 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index
-rw-r--r-- 1 root root      74 2012-02-18 03:51 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources.decomp
-rw-r--r-- 1 root root      14 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-09 11:55 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    7643 2012-02-09 11:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index
-rw-r--r-- 1 root root      72 2012-02-18 03:51 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-19 15:48 in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources.decomp
-rw-r--r-- 1 root root  100778 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_main_binary-i386_Packages
-rw-r--r-- 1 root root  478285 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    1645 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_main_i18n_Index
-rw-r--r-- 1 root root      14 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_main_source_Sources
-rw-r--r-- 1 root root       0 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root   35254 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    1491 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_multiverse_source_Sources
-rw-r--r-- 1 root root    1491 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root   29336 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_restricted_binary-i386_Packages
-rw-r--r-- 1 root root  120364 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root  134985 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root       0 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   11381 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_universe_source_Sources
-rw-r--r-- 1 root root   11381 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-backports_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      20 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    3662 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_main_i18n_Index
-rw-r--r-- 1 root root   43194 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root  163420 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root  288223 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_multiverse_i18n_Index
-rw-r--r-- 1 root root  134535 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_multiverse_source_Sources
-rw-r--r-- 1 root root  134535 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root  123294 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_restricted_binary-i386_Packages
-rw-r--r-- 1 root root  596165 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root   96407 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_restricted_i18n_Index
-rw-r--r-- 1 root root  375837 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_restricted_source_Sources
-rw-r--r-- 1 root root 1878703 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      73 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_main_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 16:42 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_main_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    1172 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_main_i18n_Index
-rw-r--r-- 1 root root   12505 2012-02-18 03:34 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 1582667 2011-10-12 23:43 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 16:42 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_multiverse_binary-i386_Packages.decomp
-rw-r--r-- 1 root root  179981 2011-10-12 23:49 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_multiverse_i18n_Index
-rw-r--r-- 1 root root    5667 2012-02-09 07:28 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_multiverse_source_Sources
-rw-r--r-- 1 root root    5667 2012-02-09 07:28 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    5267 2011-10-12 23:47 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 16:42 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_restricted_binary-i386_Packages.decomp
-rw-r--r-- 1 root root    3549 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_restricted_i18n_Index
-rw-r--r-- 1 root root      20 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_restricted_source_Sources
-rw-r--r-- 1 root root      20 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root 5792409 2011-10-12 23:49 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-19 16:42 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_universe_binary-i386_Packages.decomp
-rw-r--r-- 1 root root   50720 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_universe_i18n_Index
-rw-r--r-- 1 root root      20 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_universe_source_Sources
-rw-r--r-- 1 root root      20 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-security_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    1337 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_universe_binary-i386_Packages
-rw-r--r-- 1 root root    3179 2012-02-18 03:50 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2968 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_universe_i18n_Index
-rw-r--r-- 1 root root    3524 2012-02-16 08:29 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_universe_source_Sources
-rw-r--r-- 1 root root    3524 2012-02-16 08:29 mirrors.ubuntu.com_mirrors.txt_dists_oneiric_universe_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      14 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root      14 2011-10-24 15:51 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_main_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    6355 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_main_source_Sources
-rw-r--r-- 1 root root   25801 2012-02-18 03:45 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_main_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    6563 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   19531 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_multiverse_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    2585 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_multiverse_source_Sources
-rw-r--r-- 1 root root    9048 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_multiverse_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root    2207 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root    5172 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_restricted_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_restricted_i18n_Index
-rw-r--r-- 1 root root    6821 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_restricted_source_Sources
-rw-r--r-- 1 root root   19531 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_restricted_source_Sources.decomp.FAILED
-rw-r--r-- 1 root root      14 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root       0 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_universe_binary-i386_Packages.decomp.FAILED
-rw-r--r-- 1 root root    7643 2012-02-09 11:48 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_universe_i18n_Index
-rw-r--r-- 1 root root      20 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_universe_source_Sources
-rw-r--r-- 1 root root       0 2012-02-09 11:55 mirrors.ubuntu.com_mirrors.txt_dists_oneiric-updates_universe_source_Sources.decomp.FAILED
```

---

### Post by Peacewise on 2012-02-19
Also :
```
sudo rm /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index (1)
bash: syntax error near unexpected token `('
```

---

### Post by ajgreeny on 2012-02-19
OK, so try removing all the files in /var/lib/apt/lists/partial with ```
sudo rm /var/lib/apt/lists/partial/*
``` and try once more.  There should normally be no files in that /partial folder; any there are usually the result of a problem with updating the repositories at one point.

---

### Post by Peacewise on 2012-02-19
This is what it says now :
```
Fetched 5,849 kB in 50s (116 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index

W: Failed to fetch copy:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch copy:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Peacewise on 2012-02-19
Also i am unable to run any mp3 files
Failed to download repository information:
Check your internet connection

---

### Post by ajgreeny on 2012-02-19
I suspect your sources.list file is not correct.

Can we see the output of ```
cat /etc/apt/sources.list
``` please and ```
ls /etc/apt/sources.list.d
```

---

### Post by Peacewise on 2012-02-20
```
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```
 
and ```
ls /etc/apt/sources.list.d

``` does not give any output

---

### Post by ajgreeny on 2012-02-20
Not much wrong there, as far as I can see.

I suggest you remove any of the files that are in that /partial folder again and try a different server which you can setup from the first tab of software-sources.

This is all getting a bit baffling.

---

### Post by Peacewise on 2012-02-20
I changed the server and it somehow worked...
Neways now when i try to install any app i get this :
```
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 177052 files and directories currently installed.) 
Removing cheese ... 
Removing libcheese-gtk20 ... 
Removing libcheese1 ... 
Removing cheese-common ... 
Removing gnome-video-effects ... 
Removing libmx-1.0-2 ... 
Removing libcluttergesture-0.0.2-0 ... 
Removing libclutter-imcontext-0.1-0 ... 
Removing libclutter-gst-1.0-0 ... 
Removing libclutter-gtk-1.0-0 ... 
Removing libclutter-1.0-0 ... 
Removing libclutter-1.0-common ... 
Removing libcogl-common ... 
Removing libcogl5 ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for libglib2.0-0 ... 
Setting up flashplugin-downloader (11.1.102.55ubuntu0.11.10.1) ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Downloading... 
--2012-02-21 20:36:24--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.55.orig.tar.gz 
Connecting to 10.3.100.211:8080... connected. 
Proxy request sent, awaiting response... 404 Not Found 
2012-02-21 20:36:24 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 flashplugin-downloader 
 flashplugin-installer 
Setting up flashplugin-downloader (11.1.102.55ubuntu0.11.10.1) ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Downloading... 
--2012-02-21 20:36:25--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.55.orig.tar.gz 
Connecting to 10.3.100.211:8080... connected. 
Proxy request sent, awaiting response... 404 Not Found 
2012-02-21 20:36:25 ERROR 404: Not Found. 
 
download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of flashplugin-installer: 
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however: 
  Package flashplugin-downloader is not configured yet. 
dpkg: error processing flashplugin-installer (--configure): 
 dependency problems - leaving unconfigured 

```

---


---
title: "Ubuntu 11.04 so many failed when update"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by asiansexynine on 2011-08-03
Ubuntu 11.04 so many failed when update:
```

Err http://security.ubuntu.com natty-security/restricted Sources                                  
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com natty-security/restricted i386 Packages                            
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com natty-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.167 80]                               
Err http://th.archive.ubuntu.com natty/restricted Sources                                         
  416  Requested Range Not Satisfiable


```
```

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/th.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch http://th.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  416  Requested Range Not Satisfiable

W: Failed to fetch gzip:/var/lib/apt/lists/partial/th.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/th.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/th.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ferramroberto_java_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_n-muench_programs-ppa_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

I don't know how it work.. most of update working fine.. but only all it that i am post here i am tried often but doesn't work.

---

### Post by Duncan Williams on 2011-08-03
sounds like an internet connection issue.
As in it's saying it cannot get the packages?

---

### Post by asiansexynine on 2011-08-03
> **Duncan Williams said:**
> sounds like an internet connection issue.
As in it's saying it cannot get the packages?


I don't think so, because it's should be failed all with all package if got internet connection issue. 
but this failed from my list there try to get a package from [IP: 91.189.92.167 80]

I am search IP: 91.189.92.167 80 on google and seem not only me got this failed. but i really don't know why must be IP: 91.189.92.167 80 for up to date Ubuntu?

IP: 91.189.92.167 80 is virus?

---

### Post by Duncan Williams on 2011-08-03
I use 3g mobile broadband and my signal is sometimes erratic.
So it could download some but not all of packages in a download.

[http://www.google.com/search?q=IP:%2091.189.92.167%2080](http://www.google.com/search?q=IP:%2091.189.92.167%2080)
shows probs like your having.

---

### Post by squigles1 on 2011-09-14
Been having similar problem.
I was sent to look at this  threads:
[URL="http://ubuntuforums.org/showthread.php?t=1729381"]
http://ubuntuforums.org/showthread.php?t=1729381[/URL]

I backed up the thoughts with this thread:
[URL="http://ubuntuforums.org/showthread.php?t=1765266"]
http://ubuntuforums.org/showthread.php?t=1765266[/URL]

The advice to enter ```


sudo rm -rf /var/lib/apt/lists/partial/*
```

into the terminal seems to have corrected my error!
Good Luck

---


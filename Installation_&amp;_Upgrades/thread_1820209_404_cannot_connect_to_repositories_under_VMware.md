---
title: "404 cannot connect to repositories under VMware"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by pablohonee on 2011-08-07
Hi all,

I am trying to run ubuntu 11 under vmware server and have hit a snag that I cannot seem to google my way out of. Although I can browse the internet (I'm posting from firefox on the virtual machine now) and ping (e.g. ping google.com gives: 
```

PING google.com (74.125.93.147) 56(84) bytes of data.
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_seq=1 ttl=128 time=36.7 ms

```), I cannot use either synaptic package manager or apt-get due to problems connecting to the repositories:

```

<userid>@ubuntu:~$ sudo apt-get update
[sudo] password for <userid>: 
Ign http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security Release.gpg
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid Release
Ign http://us.archive.ubuntu.com intrepid-updates Release
Ign http://us.archive.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/main Packages
Ign http://us.archive.ubuntu.com intrepid/restricted Packages
Ign http://us.archive.ubuntu.com intrepid/main Sources
Ign http://us.archive.ubuntu.com intrepid/restricted Sources
Ign http://us.archive.ubuntu.com intrepid/universe Packages
Ign http://us.archive.ubuntu.com intrepid/universe Sources
Ign http://us.archive.ubuntu.com intrepid/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-updates/main Packages
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://us.archive.ubuntu.com intrepid-updates/main Sources
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://us.archive.ubuntu.com intrepid-updates/universe Packages
Ign http://us.archive.ubuntu.com intrepid-updates/universe Sources
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-security/main Packages
Ign http://us.archive.ubuntu.com intrepid-security/restricted Packages
Ign http://us.archive.ubuntu.com intrepid-security/main Sources
Ign http://us.archive.ubuntu.com intrepid-security/restricted Sources
Ign http://us.archive.ubuntu.com intrepid-security/universe Packages
Ign http://us.archive.ubuntu.com intrepid-security/universe Sources
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Sources
Err http://us.archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/main Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/restricted Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/universe Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://us.archive.ubuntu.com intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.92.169 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
<userid>@ubuntu:~$ 

```I have looked at a number of related posts which seem to be marked solved without a clear explanation of what was wrong or how to fix it. I am somewhat new to linux and would appreciate any help. Thanks!

---


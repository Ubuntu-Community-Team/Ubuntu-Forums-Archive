---
title: "can't update or install programs"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by mhbell on 2006-08-19
I can't update or install programs using Apt or synaptic. here is an example of what I get using Apt. I have searched the forum for a Repository List or source list with no luck. here is the error that I get when I try to update using apt and the same thing with update manager and synaptic..
Mel
:( 

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  403 Forbidden [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38) 6/Packages.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina) ry-i386/Packages.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou) rces.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour) ce/Sources.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/bi](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/bi) nary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric) ted/binary-i386/Packages.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so) urce/Sources.gz  403 Forbidden [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restric) ted/source/Sources.gz  403 Forbidden [IP: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used

---

### Post by Dr. Nick on 2006-08-19
here is  a source.list

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by K.Mandla on 2006-08-20
This is fun too:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

In any case, your output looks an awful lot like a sources.list problem.

---

### Post by tamarku on 2006-08-20
I too can't seem to run any updates.  I got the message that there was an update available but I can't get anything to download and install.

---

### Post by Dr. Nick on 2006-08-20
> **tamarku said:**
> I too can't seem to run any updates.  I got the message that there was an update available but I can't get anything to download and install.

I came up on this just today, Do you have compiz installed?

If so your synaptic is probably goofed, a compiz update updated a file that is messing up synaptic, try this to fix it

**sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4**

---


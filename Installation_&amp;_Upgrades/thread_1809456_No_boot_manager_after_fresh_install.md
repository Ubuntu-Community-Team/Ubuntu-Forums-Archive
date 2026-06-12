---
title: "No boot manager after fresh install"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by leilei1 on 2011-07-21
So  I recently ran testdisk on my hard drive in attempt to recover some files from a partition. Now I just installed ubuntu 10.04 from my flash drive to same hard drive after formatting it. When the hard drive was booted I got a message saying 1234f.  I read that this happens sometimes when you write testdisk's MBR(which I did) and that the solution was to reinstall grub2. So I followed a tutorial on reinstalling but whenever I go to run "apt-get update" it shows that the files could not be retrieved, meaning I can't even reinstall grub2.

Output from apt-get update
> 
root@ubuntu:/# apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                  
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                       
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages           
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                   
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages              
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

output from trying to install grub-pc
> 
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
\Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-pc has no installation candidate



---

### Post by Quackers on 2011-07-21
Are you connected to the internet on the affected machine?

---

### Post by leilei1 on 2011-07-23
I ended up just reinstalling Ubuntu to the entire hard drive and thankfully it boots, but only under certain conditions. Will post back if I am unable to fix the problem.

---

### Post by leilei1 on 2011-07-23
Okay so my idea didn't work. Here's the situation, I have 4 hard drives 3 with an OS and a Deskstar an ext4 partition for backup. The Ubuntu hard drive won't boot unless I set the Deskstar as first in boot priority and the Ubuntu drive as second. If I set the Ubuntu drive as first in boot priority then I get a flashing underscore on my screen and nothing happens. Is the MBR messed up on the Ubuntu drive?

---

### Post by leilei1 on 2011-07-23
So what I found was that Grub didn't install to my Ubuntu drive during installation :confused: . Thanks to an AWESOME application called Boot Repair I was able to install grub to my Ubuntu drive :D. Which also picked up that there were other OS's on my other drives so I can boot off of any hard drive through GRUB rather than editing boot priority in my BIOS.

Here's the link to the boot manager: [http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by Quackers on 2011-07-23
Sorry, I missed your previous post. 
It would appear that grub was not installed to the right drive, as you suspect.
I'm glad you found the boot repair utility solved your problems :-)
I have seen others posting similar comments, but have not tried it myself.

---


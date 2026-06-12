---
title: "install linux-686-smp (offline mode)"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by pyter on 2006-10-01
i'm trying to install this kernel (2.6.15-26-686smp) so that ubuntu can support my dual core processor.

so i did this:

```
sudo apt-get install linux-686-smp
```

and i got this:

> 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-image-2.6.15-26-686 linux-image-686
  linux-restricted-modules-2.6.15-26-686 linux-restricted-modules-686
Suggested packages:
  linux-doc-2.6.15 linux-source-2.6.15 nvidia-glx nvidia-glx-legacy
  avm-fritz-firmware-2.6.15-26
Recommended packages:
  lilo
The following NEW packages will be installed:
  linux-686-smp linux-image-2.6.15-26-686 linux-image-686
  linux-restricted-modules-2.6.15-26-686 linux-restricted-modules-686
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB of archives.
After unpacking 85.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-26-686 2.6.15-26.46
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-686 2.6.15.24
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-2.6.15-26-686 2.6.15.11-3
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-686 2.6.15.24
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-686-smp 2.6.15.24
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-686_2.6.15-26.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-686_2.6.15-26.46_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-686_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-686_2.6.15.24_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-686_2.6.15.11-3_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-686_2.6.15.11-3_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-686_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-686_2.6.15.24_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-686-smp_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-686-smp_2.6.15.24_i386.deb)  Temporary failure resolving 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

has you can see it couldn't fetch the files but that's normal because my ethernet card isn't working. and to make it work i need this kernel!

i'm following the instructions on this website:
[http://www.thefuckingshit.org/?p=425](http://www.thefuckingshit.org/?p=425)


is there any way to make it fetch the files on my home folder?

and there's another thing... some files it asks for doesn't exit anymore. i had to download others.

please help me!

---


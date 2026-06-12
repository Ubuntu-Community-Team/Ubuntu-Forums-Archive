---
title: "problem in installing g++ compiler"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by ubantuooo on 2010-03-08
i'm a c++ user but new on gcc compiler. so while installing g++ compiler i follwed the previous threads for installing g++ compiler by using the following commandline:-

sudo apt-get update
sudo apt-get install build-essential
gcc -v

roshni@roshni-laptop:~$ g++ vowel.cpp
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found
roshni@roshni-laptop:~$ gcc vowel.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
roshni@roshni-laptop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IN 
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IN
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release.gpg                       
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
roshni@roshni-laptop:~$ n
bash: n: command not found
roshni@roshni-laptop:~$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
roshni@roshni-laptop:~$ y
bash: y: command not found
roshni@roshni-laptop:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
roshni@roshni-laptop:~$ 


please help me out....
what will i do for installing g++ compiler....
and THNAX in advance...;)

---

### Post by khelben1979 on 2010-03-08
Ubuntu cannot access the servers. This means you need to try the same thing at a later time. Just keep on trying until it works would be my advice.

---

### Post by ORBAT on 2010-03-08
> **ubantuooo said:**
> 
roshni@roshni-laptop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN
  Could not resolve 'security.ubuntu.com'

...

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I think khelben1979 is incorrect on this one. Waiting won't do a thing for you since it looks like your network connection isn't working. apt-get failed during DNS resolution, which means that even DNS lookups aren't going anywhere. Are your network settings OK?

Plus, you were trying to run apt-get while another package manager was open, which won't work. Did you have Synaptic or something like that open at the same time?

---


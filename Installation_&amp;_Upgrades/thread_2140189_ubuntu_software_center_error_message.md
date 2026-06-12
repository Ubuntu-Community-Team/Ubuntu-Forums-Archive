---
title: "ubuntu software center error message"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by mzar720 on 2013-04-28
i have installed ubuntu last version 13.04, i tried to install google chrome but i failed may be because i am using 64-bit version, but now i am unable to install any application because now i have problem with ubuntu software center when i open it i got this error message "no software can't be installed because the is a problem with the software currently installed, do you want to repair this problem now?'' then i press repair, but it failed and i got this one ''Package operation failed The installation or removal of a software package failed. 
installArchives() failed: Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin


can you plz help me with this problem, 

thanks

---

### Post by mzar720 on 2013-04-29
Up!!!

---

### Post by davidbaumann on 2013-04-29
What does following (run in Console)
```
sudo apt-get -f install
```

David.

---

### Post by mzar720 on 2013-04-29
thanks david, this what i got
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfaac0 libmjpegtools-1.9 libquicktime2 libsidplay1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc-bin
The following NEW packages will be installed:
  libc-bin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,180 kB of archives.
After this operation, 3,564 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)


---

